# SageMaker-Security-templates
This is a Set of CloudFormation templates to quickly set up secure SageMaker Notebook Instances.

This currently uses infrastructure-as-code to automatically provision secure, encrypted and network isolated notebook and project environments. The templates consist of the following

1. product_template.yaml: Main template whihc launches a set of nested templates to provision the products in their entirety
2. vpc_template.yaml: Creates a secure project VPC without internet connectivity and a private subnet. This is the secure project environment.
3. iam_template.yaml: provisions the fine grained IAM role for the SageMaker notebook instance. This role only allows SageMaker API calls via the respective subnets and access only to project buckets. Additional API calls can be denied based on customer requirement.
4. s3_template.yaml: Creates the project S3 buckets, ensures that versioning is enabled and they are encrypted using Customer managed Customer master key (CMK) using KMS
5. sagemaker_tempalate.yaml: Provisions a notebook with encrypted EBS volume, attached to the VPC and Subnets having no internet access and proper IAM role. 
