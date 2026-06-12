---
title: "ec2: Creating a bundle?"
date: 2009-05-17
forum: Server Platforms
---

### Post by uri.london on 2009-05-17
Hi,
 
I've followed the instructions from EC2 Starter Guide ([here]("https://help.ubuntu.com/community/EC2StartersGuide")). Everything works great!!!
 
Next step, I've made some changes, installed few packages (most notably: MySQL), and still - everything is still working just great.
 
Next, I want to create a private AMI from my instance, so I could lanch an instance with these settings. I'm using Elastic Fox.
 
From Elastic Fox, right click on the instance, I find that 'Bundle into an AMI' is grayed out. This is where I'll greatly appreciate some help.
 
 
Thanks
u.

---

### Post by s0na on 2010-01-04
I don't believe this function is accessible from Elasticfox or the AWS console at the moment for Linux/Unix instances. You can bundle your instance by sshing to it and using AMI ec2 command line apis.

[http://docs.amazonwebservices.com/AWSEC2/latest/GettingStartedGuide/index.html?creating-an-image.html](http://docs.amazonwebservices.com/AWSEC2/latest/GettingStartedGuide/index.html?creating-an-image.html)

---

