---
title: "Amazon S3 host of wordpress site"
date: 2010-11-16
forum: Ubuntu Cloud and Juju
---

### Post by Kubureaucrat on 2010-11-16
Hello.  I want to host a wordpress site through Amazon S3 or some Amazon service.  Specifically I want to host with Amazon because I will be (legally) selling enormous files, and it doesn't make sense for me to try to do that elsewhere due to bandwidth constraints.  Also I expect to use some of Amazon's expiring links since, well, the links have to change after sales.  My current host is great (steadfast.net, by far the best I've ever had), but it can't handle the bandwidth of huge files, and I have to jump through all sorts of crazy hoops in order to try to sell media that is hosted elsewhere.  So I'd rather just do it all in one place.

I figure I will do an Ubuntu server with Wordpress.  However, I can't find the right resource, step by step, for migrating a Wordpress site to an Amazon S3 host under Ubuntu.  Seems like there must be something out there, but I haven't found it.  

Parenthetically, I intend to use the most recent LTS upon install, and also keep the install very bare bones.  To that end, maybe even go Xubuntu?  Advice welcome.

Can someone point it out to me?

Thanks

---

### Post by kim0 on 2010-11-17
I got something lighter than Xubuntu for you! Ubuntu-server. Find the latest AMIs at
[http://uec-images.ubuntu.com/server/releases/lucid/release/](http://uec-images.ubuntu.com/server/releases/lucid/release/)

So basically, you pick an AMI (example: ami-da0cf8b3) and you launch it, that's it. Once you launch your ec2 instance, you get a normal linux server, so migrating your wordpress to amazon is no different than migrating to any other linux server. Hosting your files on S3 is a "separate" step. Think of S3 as a CDN that could really be used with any other hosting provider (ec2 or otherwise). You may also be interested in Amazon's torrent access to large files (google it)

Have fun

---

### Post by Kubureaucrat on 2010-11-17
Thank you.  The point of my trying to move to Amazon hosting is to avoid file transfer size issues.  I know that S3 has those great hosting rates.  Does EC2 do the same?  

I want everything hosted at the same location, as I'm trying to avoid the problems inherent in trying to sell files (with randomized links) hosted elsewhere.

---

### Post by kim0 on 2010-11-18
Hi, I think you're a bit confused. EC2 is for providing a virtual server to run wordpress itself on. Yes the rates are good, check out the pricing at
[http://aws.amazon.com/ec2/pricing/](http://aws.amazon.com/ec2/pricing/)

S3 is simply a file storage service. You can use it with EC2 or with any other hosting provider. Although indeed it may somehow be simpler to host everything with Amazon

---

### Post by Kubureaucrat on 2010-11-18
Thanks.  Yes, I guess you're right.  I was hoping the two could somehow easily be combined. 

I don't have any problem selling directly from my current site as is, except for the file sizes.

Ultimately, I’m hoping to use your S3 expiring URL generator to sell (legally) enormous video files hosted on S3.

Sort of a combination of this
[http://wordpress.org/extend/plugins/amazon-s3-url-generator/download/](http://wordpress.org/extend/plugins/amazon-s3-url-generator/download/)

and this
[http://wordpress.org/extend/plugins/*****/](http://wordpress.org/extend/plugins/*****/)

I'll let things be after that, as I realize it's more a Wordpress and S3 question than an Ubuntu question.  But if anyone has any ideas please let me know.

Thank you.

---

