# Azure End-To-End Data Engineering Project Report

This report outlines the steps I followed to complete the Azure End-to-End Data Engineering Project. The project focuses on building a data pipeline using Azure services, starting from data ingestion, followed by transformation, storage, orchestration, and visualization. The goal is to create a scalable and automated data processing pipeline.

## Dataset

The dataset used in this project is the AdventureWorks dataset from Kaggle. It is a widely-used sample database that contains transactional data for a fictitious multinational manufacturing company. It includes tables for sales, products, customers, and employees.

### Key Tables:
- SalesOrderHeader
- SalesOrderDetail
- Product
- Customer
- Employee

## Project Setup

### 2.1 Environment Setup
- **Azure Subscription**: Used an existing Azure account for accessing required services.
- **Resource Group**: Created a new resource group to organize all resources related to the project.

### Blob Storage Setup
- Uploaded the AdventureWorks dataset to Azure Blob Storage in CSV format for easy access and manipulation.

### Creating a Dynamic Pipeline in Azure Data Factory
To streamline the data ingestion process, I created a dynamic pipeline in Azure Data Factory (ADF). This pipeline was designed to automatically ingest all files from the Blob Storage container without the need for hardcoding individual file names.

#### Steps:
1. **Get List of Files**: Used the Get Metadata activity to dynamically list all files within the Blob Storage container, automatically detecting new or updated files.
2. **ForEach Activity**: Iterated through each file in the container using the ForEach activity and processed them with the Copy Data activity, ingesting them into Azure Data Lake or Azure SQL Database.
3. **Dynamic Parameters**: Utilized parameters within the pipeline to pass dynamic values such as file names and paths, ensuring flexibility and scalability.

### Data Transformation

The AdventureWorks dataset was analyzed for relevant tables and columns for transformation. The key transformation tasks included:
- **Data Cleansing**: Removing records with missing values or duplicates, particularly for critical fields like order IDs or customer details.
- **Data Aggregation**: Combining multiple tables to derive insights such as total sales by customer or product category.
- **Feature Engineering**: Creating new columns by combining SalesOrderDetail line items and grouping by order.

Using Azure Databricks, I applied PySpark for data transformations, including:
- Join operations to combine related tables
- Data filtering to clean out incomplete or incorrect records
- GroupBy operations to summarize data by customer, region, or product

### Data Analytics with Azure Synapse Analytics
I used Azure Synapse Analytics to run SQL-based queries on the transformed data and derive business insights. Synapse was integrated with both Data Lake Storage and Azure SQL Database for seamless querying.

### Error Handling and Monitoring
- **Azure Logic Apps**: Configured to send automated notifications in case of pipeline failures, ensuring timely issue resolution.
- **Azure Monitor**: Set up to track pipeline performance, resource utilization, and error tracking.

## Challenges & Learnings

### Challenges:
- **Data Quality Issues**: Encountered missing or inconsistent data, which required careful handling during the transformation phase.
- **Pipeline Orchestration**: Coordinating the data ingestion, transformation, and loading steps effectively was a key challenge, particularly with large datasets.

### Learnings:
- Gained hands-on experience with core Azure services like Azure Data Factory, Databricks, and Synapse.
- Enhanced skills in automation, monitoring, and error handling within Azure.

## Conclusion

The Azure End-to-End Data Engineering project successfully implemented an automated data pipeline using a range of Azure services. This project strengthened my expertise in data ingestion, transformation, orchestration, and reporting, which will be valuable for future data engineering tasks.
