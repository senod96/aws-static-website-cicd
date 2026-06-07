# AWS Static Website CI/CD Deployment

## Overview

This project demonstrates a complete cloud-based static website deployment pipeline using AWS and GitHub Actions.

The website is hosted on Amazon S3 and delivered through Amazon CloudFront. Deployments are fully automated using GitHub Actions and secure AWS OIDC authentication, eliminating the need for long-lived AWS access keys.

## Architecture

```text
Developer
    ↓
Git Push
    ↓
GitHub Actions
    ↓
AWS OIDC Authentication
    ↓
IAM Role
    ↓
Amazon S3
    ↓
CloudFront Cache Invalidation
    ↓
CloudFront Distribution
    ↓
Users
```

## Technologies Used

* Amazon S3
* Amazon CloudFront
* AWS IAM
* AWS OIDC Federation
* GitHub Actions
* HTML
* CSS
* JavaScript

## Features

* Static website hosting on Amazon S3
* Global content delivery using CloudFront
* Private S3 bucket access using Origin Access Control (OAC)
* Automated deployment through GitHub Actions
* Secure AWS authentication using OIDC
* Automated CloudFront cache invalidation
* Infrastructure secured using least-privilege IAM permissions

## Project Setup

### 1. Create S3 Bucket

Create a private S3 bucket to store website files.

### 2. Configure CloudFront

Create a CloudFront distribution and configure:

* Origin Access Control (OAC)
* Default root object (`index.html`)

### 3. Configure IAM Role

Create an IAM role for GitHub Actions using:

* OIDC provider
* Least privilege permissions

### 4. Configure GitHub Actions

Create a workflow that:

* Authenticates with AWS
* Uploads website files to S3
* Invalidates CloudFront cache

## Deployment Workflow

Every push to the `master` branch automatically:

1. Triggers GitHub Actions
2. Authenticates to AWS using OIDC
3. Synchronizes website files to S3
4. Creates a CloudFront invalidation
5. Publishes the latest version of the website

## Lessons Learned

During this project I gained hands-on experience with:

* AWS CloudFront configuration
* S3 bucket policies
* Origin Access Control (OAC)
* IAM permissions and least-privilege access
* OIDC federation between GitHub and AWS
* CI/CD pipeline implementation
* Troubleshooting CloudFront AccessDenied errors
* Cloud deployment automation

## Live Demo

CloudFront URL:

https://d2ukge4ij8k36t.cloudfront.net

## Author

Built as a cloud engineering learning project using AWS Free Tier services.
