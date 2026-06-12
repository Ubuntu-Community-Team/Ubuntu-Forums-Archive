---
title: "Cloud Computing not able to restart the Instance"
date: 2010-05-10
forum: Server Platforms
---

### Post by gillsukhvir on 2010-05-10
Hi ,

I have just started working on the Cloud Computing  and have been to get the Cloud Configured uisng Ubuntu Server CD 10.04 LTS having eucalyptus Ver 1.6.2 

I have used the bundled image with eucalyptus  and have been able to run the same successfully  , i am even able to login to this instance .

Now i have one small query . I have shutdown the instance by loggin as root user and am not able to get the same booted up .

When i re-run the instance using the instance ID which was described by "euca-describe-instance" i get below error

ImageVerify: Failed to find disk image: i-513D0987

Now to my knowledge when we run the image using "euca-run-instance" the image gets deployed to the Node under /var/lib/eucalyptus/instances

I wanted to know 

1. How will the controller access the  image which has been terminated or shutdown

2. Is there some other process to shutdown the running instance . Am i missing something .

3. Was curios to know when we run the image from the contoroller then in case we have a setup having 2 Nodes then will this image get pushed to both these nodes and will be accessible even if one of the Node has been shutdown

Will appreciate your help with this regards since  i have been stuck with the management of the VM's 


Regards ,
Gill Sukhvir Singh

---

