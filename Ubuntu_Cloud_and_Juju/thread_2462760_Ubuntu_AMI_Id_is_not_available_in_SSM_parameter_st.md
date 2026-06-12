---
title: "Ubuntu AMI Id is not available in SSM parameter store for AWS Osaka region"
date: 2021-05-27
forum: Ubuntu Cloud and Juju
---

### Post by pankajc123 on 2021-05-27
Hello,
We are using AWS SSM parameter store to retrieve latest Ubuntu AMI id in our AWS CloudFormation templates. AWS SSM parameter store we are using to retrieve latest Ubuntu AMI id is   "/aws/service/canonical/ubuntu/server/18.04/stable/current/amd64/hvm/ebs-gp2/ami-id".

I have referred to article below.
 [https://discourse.ubuntu.com/t/finding-ubuntu-images-with-the-aws-ssm-parameter-store/15507]("https://urldefense.com/v3/__https:/discourse.ubuntu.com/t/finding-ubuntu-images-with-the-aws-ssm-parameter-store/15507__;!!CKZwjTOV!imBm_v3V-3mNGPkdjB72msI97vQxRiSYEZDQN-vq-F6jqMMRJJntkkLGXtfV6w$")
 
We have observed that we are able to retrieve latest Ubuntu AMI Id for majority of AWS regions in public cloud except "Osaka" AWS region and AWS Gov Cloud regions (us-gov-east-1 and us-gov-east-2). Can you please help to make sure if AWS SSM parameter with appropriate AMI Id is updated for "Osaka" AWS region and AWS Gov Cloud regions (us-gov-east-1 and us-gov-east-2)?
 
I am using AWS CLI command below. (This is just for your reference).
 
aws ssm get-parameters --names /aws/service/canonical/ubuntu/server/18.04/stable/current/amd64/hvm/ebs-gp2/ami-id --region ap-northeast-3
 
Thanks.
 
Best Regards
Pankaj

---

