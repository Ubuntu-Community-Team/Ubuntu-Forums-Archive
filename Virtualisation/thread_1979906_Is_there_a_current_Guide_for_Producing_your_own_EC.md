---
title: "Is there a current Guide for Producing your own EC2 AMI from scratch."
date: 2012-05-14
forum: Virtualisation
---

### Post by bmullan on 2012-05-14
Can someone point to a "current" guide for producing your own AWS EC2 AMI from scratch on your PC.   [I]Note:  I am not talking about simply cloning an existing EC2 AMI here but doing it from say your own home PC.
[/I]
Last time I had a need to do this was a couple years ago and then it only required the following three basic API commands before I had an AMI I could launch.   But today I know there is more to it because of changes in AWS and in Ubuntu itself?

ec2-bundle-image
[http://docs.amazonwebservices.com/AmazonEC2/dg/2006-10-01/CLTRG-ami-bundle-image.html]("http://docs.amazonwebservices.com/AmazonEC2/dg/2006-10-01/CLTRG-ami-bundle-image.html")

ec2-upload-bundle
[http://docs.amazonwebservices.com/AmazonEC2/dg/2006-10-01/CLTRG-ami-upload-bundle.html]("http://docs.amazonwebservices.com/AmazonEC2/dg/2006-10-01/CLTRG-ami-upload-bundle.html")

ec2-register
[http://docs.amazonwebservices.com/AWSEC2/latest/CommandLineReference/ApiReference-cmd-RegisterImage.html]("http://docs.amazonwebservices.com/AWSEC2/latest/CommandLineReference/ApiReference-cmd-RegisterImage.html")

---

