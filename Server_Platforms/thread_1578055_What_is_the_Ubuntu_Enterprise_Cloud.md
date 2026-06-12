---
title: "What is the Ubuntu Enterprise Cloud?"
date: 2010-09-19
forum: Server Platforms
---

### Post by kevin11951 on 2010-09-19
I have read just about every page about the UEC project, and I now know everything about it, except...  WHAT IT DOES!

I can't seem to find a coherent example of what it does.  

To the best of my understanding, it runs a virtual machine across multiple servers.  Allowing the VM to use the RAM, CPU, and HDD resourced on all servers involved.

A bit like a super computer cluster.

---

### Post by Sporkman on 2010-09-19
It's a product that uses several in-vogue buzzwords.

---

### Post by uRock on 2010-09-19
Moved to Server Platforms. You might get better answers to your question here.

---

### Post by BkkBonanza on 2010-09-19
UEC is Canonical's version of Amazon EC2. It's for people (businesses) that need access to varying amounts of server resources on an as-needed pay-as-you-go basis. For your typical one server web site it's not going to interest you. 

But if you want to build an application/web site that can "Scale up" on demand without having to manage clusters of real hardware then it's a great fit. It allows you to start small, design for scaling, and when the masses hit your site you can (in theory) click a few buttons to add new servers, load balance, scale up and not suffer the infamous "slashdot effect". 

It also integrates with CDN (content delivery network) functions for maintaining global copies of "assets" (images/video/data) in multiple locations to deliver them quickly.

I use EC2 for testing/learning and will keep a "dormant" almost-live copy of my web server there so if my VPS server (which is cheaper and better performing for the price) goes down I can switch over and launch my failover backup in minutes. I also use S3 for automated server backups.

I'm not sure what differences there are between UEC and EC2, if any. I think they're just trying to hook into what many see as the future of hosting web apps. No more buying rackspace, co-locating machines, negotiating contracts, having spare capacity sitting idle ready for the "blitz". Just pay as you need, start/stop new servers by remote control and let Amazon/Canonical manage the hardware, networking, and backup/redundancy issues.

I've tested the performance on the small/micro level EC2 instances and they pale in comparison to my $10/mo VPS account. So the value isn't there from that point of view. Where it shines is in scaling, redundancy, reliability, availability.

---

### Post by kevin11951 on 2010-09-19
> **BkkBonanza said:**
> UEC is Canonical's version of Amazon EC2. It's for people (businesses) that need access to varying amounts of server resources on an as-needed pay-as-you-go basis. For your typical one server web site it's not going to interest you. 

But if you want to build an application/web site that can "Scale up" on demand without having to manage clusters of real hardware then it's a great fit. It allows you to start small, design for scaling, and when the masses hit your site you can (in theory) click a few buttons to add new servers, load balance, scale up and not suffer the infamous "slashdot effect". 

It also integrates with CDN (content delivery network) functions for maintaining global copies of "assets" (images/video/data) in multiple locations to deliver them quickly.

I use EC2 for testing/learning and will keep a "dormant" almost-live copy of my web server there so if my VPS server (which is cheaper and better performing for the price) goes down I can switch over and launch my failover backup in minutes. I also use S3 for automated server backups.

I'm not sure what differences there are between UEC and EC2, if any. I think they're just trying to hook into what many see as the future of hosting web apps. No more buying rackspace, co-locating machines, negotiating contracts, having spare capacity sitting idle ready for the "blitz". Just pay as you need, start/stop new servers by remote control and let Amazon/Canonical manage the hardware, networking, and backup/redundancy issues.

I've tested the performance on the small/micro level EC2 instances and they pale in comparison to my $10/mo VPS account. So the value isn't there from that point of view. Where it shines is in scaling, redundancy, reliability, availability.

Um, Ok...

Let me put it this way, right now I am working for a local high school to make a support ticket system, and knowledge base.  Right now only a few teachers are using it, but soon it will be hundreds (its a very large school).  I am looking for an option for when we grow out of one server.

Is UEC an option?

---

### Post by BkkBonanza on 2010-09-19
It really depends on how many servers you "figure" you will need and whether you expect the "load" to be unpredictable over time. If you can project how much you'll need and plan for it well in advance and don't expect it to drop out, you'd likely be better just budgeting fixed resources for it. A few hundred users isn't much unless the application is either poorly written or just very intensive.

It probably does make sense if you don't want to bother buying servers, and later buying more, or if the "requisition" process is a hassle. With something like EC2 you can rent "X" amount of cpu speed/disk space, and as needs grow just click a few buttons for "X+N" amount of cpu speed/disk space. ie. you can start cheap and add as needed without committing to buying hardware and rackspace, bandwidth etc.

It's well suited for developers who don't really know what they need yet. 

The application must be written with scaling in mind. For example, you really have to stick to some rules like only using POST for data updates, and GET for data retrievals because later you will want to proxy POSTs to the server doing database "master" (insert/update) duties, whereas GETs can be shared over many servers doing read-only. Likewise images and static content can be shared over many servers for load balancing. If you don't plan for these basics and build it into the code then it becomes difficult later when scaling up to many servers to handle load.

But a few hundred teachers doesn't sound like more load than one server could handle just by scaling up to higher cpu speeds as needed. Busy web server clusters handles hundreds of thousands, to millions of users, and these are more typical of where cloud applications make sense. With your app you would gain if you can rent the small size server, and when you find it slow a few clicks will get you the medium size server to improve speed. And if needed one day you click/click again to the high speed server. All without buying/backing up/moving hardware and without downtime.

eg. some corp like smugmug.com (who use EC2) starts small with hundreds of users and one day they make the headlines, suddenly 20,000 users want to sign up, and next week over a 100,000. How can you buy and set up servers to handle that in time? This is where cloud resources make sense, very fast scaling (when the app is written to scale). Next month they crap out and they're back down to 10,000 - aren't they glad they didn't just buy a cluster of 50 machines... etc.

Sure, UEC or EC2 is an option. You have to think through your own application to know if it makes sense for you.

---

### Post by kim0 on 2010-09-20
Check out my reply here
[http://ubuntuforums.org/showpost.php?p=9867510&postcount=5](http://ubuntuforums.org/showpost.php?p=9867510&postcount=5)

---

