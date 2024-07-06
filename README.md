# Spotify Data Analysis Pipeline

This repository contains the code and configurations for a robust data pipeline that extracts, transforms, and loads Spotify data using AWS services. This serverless architecture is designed for scalability and efficient data processing.

## System Architecture

![IMG_0502](https://github.com/pgrarchives/aws-etl-datapipeline/assets/112724112/d4dbb7a0-8357-4e5c-bcf9-2d0da1dc3545)

## Components

### 1. Data Extraction
- **Source**: Spotify API
- **Tool**: AWS Lambda
- **Description**: A Python script runs within AWS Lambda, triggered daily by AWS CloudWatch, to fetch data from the Spotify API.

![image](https://github.com/pgrarchives/aws-etl-datapipeline/assets/112724112/13dcb0a2-0ca6-4b24-bbd0-644ab89981b4)

### 2. Data Storage
- **Storage**: AWS S3
- **Description**: Raw data fetched from Spotify is stored in JSON format in an S3 bucket. Post-transformation, data is stored in a structured format in a separate S3 bucket.

![image](https://github.com/pgrarchives/aws-etl-datapipeline/assets/112724112/448c002e-1b2f-4108-84fc-3c66170c33aa)

### 3. Data Transformation
- **Tool**: AWS Lambda
- **Description**: Another Lambda function is triggered to transform the raw JSON data into a structured format suitable for analysis.

![image](https://github.com/pgrarchives/aws-etl-datapipeline/assets/112724112/d95b7912-2741-4ce9-9fa7-e2fa1372eaaa)

### 4. Data Loading and Cataloging
- **Tool**: AWS Glue
- **Description**: A Glue Crawler updates the AWS Glue Data Catalog with the new schema after transformations. The catalog is used for managing and accessing data schema information.

![image](https://github.com/pgrarchives/aws-etl-datapipeline/assets/112724112/76f2c163-98c1-45e0-adfd-040eb659c93c)

### 5. Data Querying
- **Tool**: AWS Athena
- **Description**: Data stored in S3 can be queried using SQL through AWS Athena, providing a powerful interface for running ad-hoc queries and generating reports.

![image](https://github.com/pgrarchives/aws-etl-datapipeline/assets/112724112/519f0a41-be74-49f1-a7fe-6d4cf44b73f4)

## Setup Instructions

1. **Configure AWS Services**:
   - Ensure that AWS IAM roles, Lambda, S3, Glue, and Athena are properly set up with the necessary permissions.
2. **Deploy the Lambda Functions**:
   - Deploy Python scripts that interact with the Spotify API and manage data transformations.
3. **Schedule Jobs**:
   - Set CloudWatch to trigger the extraction and transformation Lambda functions as required.
4. **Run Glue Crawler**:
   - Configure and run the AWS Glue Crawler to maintain the data schema in the Data Catalog.

## Usage

- Detailed usage instructions and examples of how to query the data with Athena will be provided in the `docs` directory.

