---
title: "Amazon EC2 Installs On Free Tier - Not Exactly Free"
date: 2011-04-28
forum: Server Platforms
---

### Post by Chromag on 2011-04-28
For those thinking about installing an Ubuntu Server AMI instance on Amazon EC2 under the free tier plan - be warned that you will be charged for bandwidth when running apt-get.

I'm trying to figure out if there is a way around this.  Basically, from what I can tell by posts on Amazon's forums, is that with the free tier you get 10GB in and 10GB out per month.  One of the exceptions to this is when you're transferring data from another EC2 instance in a different zone.

I didn't think I was doing this until I noticed Amazon charged me a whopping $0.01 the day I installed and updated the instance.  Apparently the default server that Ubuntu uses to pull down updates with apt-get is hosted as an EC2 instance, so I got charged for that apt-get data transfer.

Is there an Ubuntu Server update server that is NOT hosted by EC2 that I could use so that I won't get charged by Amazon?

Thanks.

---

### Post by TCAllen07 on 2011-09-12
I was doing some similar work of my own and found a few things.

According to this [short blog post]("http://zachzimm.com/blog/?p=16"), you should be able to re-direct where you get your updates to a public mirror. Apparently Ubuntu's Server AMI is automatically set to link to their **own** EC2 instance. 

-Trevor

---

### Post by TCAllen07 on 2011-09-12
Oh, and [this guy's blog post ]("http://mhlakhani.com/blog/2011/01/hidden-charges-aws-free-tier/")goes into a lot more detail. He finds that in the end, Amazon just forgives the 1-cent charge anyway, which makes sense seeing as the fees from credit card company for charge one cent would make the charge it virtually pointless!

---

### Post by Habitual on 2011-09-12
[http://alestic.com/](http://alestic.com/)

---

