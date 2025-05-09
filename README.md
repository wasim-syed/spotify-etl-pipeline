# Spotify ETL Pipeline Project
## Description
This project outlines the development of a fully automated Extract, Transform, Load (ETL) pipeline to ingest, process, and catalog music-related data from the Spotify API, culminating in an analytical-ready dataset.

## Data Flow within the Pipeline:
### 1. Data Extraction (AWS Lambda - Triggered Daily by Amazon CloudWatch):
A Python-based AWS Lambda function is scheduled to execute daily via Amazon CloudWatch Events. This function interacts with the Spotify API to extract raw data pertaining to various music entities.

### 2. Raw Data Storage (Amazon S3): 
The extracted raw data, in its native JSON format, is then stored in an Amazon S3 bucket designated for raw data.

### 3. Data Transformation (AWS Lambda - Triggered by S3 Object Creation):
Upon the successful creation of new data objects in the raw data S3 bucket, an S3 event trigger initiates an AWS Lambda function. This function transforms the raw data into a structured and optimized format.
#### Transformation steps include:
-> Data cleaning (handling missing values and inconsistencies)

-> Data-type conversions

-> Data enrichment (joining related data if necessary)

-> Data shaping and flattening of complex structures

### 4. Transformed Data Storage (Amazon S3):
This Amazon S3 bucket stores the clean, structured, and transformed data, ready for schema inference and cataloging.

### 5. Schema Inference and Cataloging (AWS Glue Crawler):
An AWS Glue Crawler automatically crawls the transformed data stored in the designated S3 bucket. The crawler analyzes the data format and infers its schema. This inferred schema is then populated into the AWS Glue Data Catalog, creating metadata tables that describe the structure and properties of the transformed data.

### 6. Data Analysis (Amazon Athena):
Finally, Amazon Athena, a serverless interactive query service, is used to analyze the cataloged data in the transformed S3 bucket. Utilizing standard SQL, analysts and stakeholders can directly query the data without the need for setting up or managing any infrastructure.

### Dataset/API 
[Spotify API](https://developer.spotify.com/documentation/web-api/)

### Installed Packages
```
pip install pandas
pip install numpy
pip install spotipy
```
