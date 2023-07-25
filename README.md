# David Hello Node - Module 3.5

## Step-by-step how to create an image to be deployed on AWS ECR
1. Ensure to have AmazonEC2ContainerRegistryPowerUser permissions

2. Authentication / Authorization to ECR
- For Public Repositories, permission needed :
> ecr-public:GetAuthorizationToken

> sts:getservicebearertoken

> **Command:**
```sh
aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/<'registry alias'>
IAM Policy: AmazonElasticContainerRegistryPublicPowerUser (AWS Managed Policy)
```

- For Private Repositories, permission needed :
> ecr:GetAuthorizationToken

> **Command :**
 ```sh
 aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin <"aws account number">.dkr.ecr.ap-southeast-1.amazonaws.com
IAM Policy: AmazonEC2ContainerRegistryPowerUser (AWS Managed Policy)
```

3. Build and Push Image to Privatre ECR
- **Command to build an image**
```sh
docker build -t <IMAGE_NAME>:<IMAGE_TAG> .
``` 
- **Command to build an image**
```sh
docker build -t <IMAGE_NAME>:<IMAGE_TAG> .
```
- **Command example with my image**
```sh
docker build -t simple-app-image .
```
- **Command to tag an image**
```sh
docker tag <IMAGE_NAME>:<IMAGE_TAG>  <REPOSITORY_URI>:<IMAGE_TAG>
```
- **Command example with our image and repository**
```sh
docker tag simple-app-image:latest <"account no.">.dkr.ecr.ap-southeast-1.amazonaws.com/<REPOSITORY_NAME>:latest
```
- **Command to push image:**
```sh
docker push <account no.>.dkr.ecr.ap-southeast-1.amazonaws.com/<REPOSITORY_NAME>:latest
```