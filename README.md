

# AWS Lambda Trigger on S3 Bucket Creation

## Project Overview

This project demonstrates how to set up an AWS Lambda function to trigger on S3 bucket creation events. The Lambda function logs information about the event and can be customized to perform specific actions. Follow the steps below to configure the project.

## Steps

### Step 1: Sign in to your AWS Account

- Access the AWS Management Console.
- Log in to the AWS Console.

### Step 2: Set Up IAM Role

1. Navigate to IAM:
   - Go to IAM.

2. Create IAM Role:
   - Choose Lambda service, attach `AWSLambdaBasicExecutionRole` and `AmazonS3ReadOnlyAccess`.
   - Name the role (e.g., `LambdaS3Role`).

### Step 3: Create Lambda Function

1. Navigate to Lambda:
   - Go to Lambda.

2. Create Lambda Function:
   - Choose Python runtime, use the IAM role, and create.

3. Configure Function Code:
   - Replace the default code with the provided Python code:
   
     ```python
     import json
     
     def lambda_handler(event, context):
         # Log the event information
         print("S3 bucket creation event:", json.dumps(event, indent=2))
         # Add your custom logic here
         return {
             'statusCode': 200,
             'body': json.dumps('Lambda function executed successfully!')
         }
     ```
   
     **Note:** Remove the default code.

### Step 4: Add Event Notification to S3 Bucket

1. Navigate to S3:
   - Go to S3.

2. Configure Event Notification:
   - Select the S3 bucket (create one if not available).
   - Under "Event notifications," click "Create" and configure.

3. Specify Events and Destination:
   - Choose "All objects create events" and select the Lambda function.

4. Review and Save:
   - Review settings and save changes.

### Step 5: Test the Setup

1. Upload File to S3 Bucket:
   - Go to the S3 Console.
   - Upload a file to the bucket.

2. Check Lambda Logs:
   - Go to the Lambda Console.
   - Open your function, navigate to "Monitoring," and check CloudWatch Logs.

3. Review Lambda Output:
   - Inspect CloudWatch Logs for Lambda function execution details.


