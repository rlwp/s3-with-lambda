# s3-with-lambda
For the assignment 2.12

**1. Purpose of the Execution Role on the Lambda Function**
The execution role (also known as the IAM role) on a Lambda function defines the permissions that the Lambda function has when it executes. This role allows the function to interact with other AWS services and resources. For example, if your Lambda function needs to read from or write to an S3 bucket, the execution role must have the necessary permissions to perform those actions.

**2. Purpose of the Resource-Based Policy on the Lambda Function**
A resource-based policy on the Lambda function specifies who (which AWS accounts, IAM users, or roles) is allowed to invoke the Lambda function. This policy ensures that only authorized entities can trigger and execute the Lambda function. It is particularly useful for cross-account access, where entities outside the Lambda function's AWS account need to be granted permission to invoke the function.

**3. Updates Needed for the Lambda Function to Upload a File into an S3 Bucket**
**a.** Needed Update on the Execution Role
To allow the Lambda function to upload a file into an S3 bucket, you need to update the execution role with the appropriate permissions. Specifically, you should add an IAM policy to the execution role that grants `s3:PutObject` permission for the target S3 bucket. This allows the Lambda function to upload objects (files) to the specified bucket.

**b.** New Resource-Based Policy (if any)
If the Lambda function needs to be invoked by entities outside its own AWS account or by specific AWS services (e.g., S3 event notifications), you may need to update the resource-based policy on the Lambda function. For example, if S3 bucket event notifications are set up to trigger the Lambda function, you need to add a policy statement that allows the S3 bucket to invoke the Lambda function.
