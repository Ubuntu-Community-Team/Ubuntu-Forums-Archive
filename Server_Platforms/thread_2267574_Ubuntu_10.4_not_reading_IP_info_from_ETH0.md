---
title: "Ubuntu 10.4 not reading IP info from ETH0"
date: 2015-03-02
forum: Server Platforms
---

### Post by PhoneTech on 2015-03-02
Hello everyone,




I have a very strange issue hoping someone can help with as I spent hours already trying to figure it out.


First off I am running Ubuntu 10.4 on a server that's been running good for years with not one issue. Just yesterday I wanted to patch it up for the Ghost virus and also thought it would be a good idea to upgrade the kernel since its been a while as well. I ran commands below.


sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade


Both Ghost and Kernel upgrade completed good no issues. I restart and boom lose internet and my SSH goes down. I logged in local and when I run ip add show ETH0 where once had all my IP info is blank with state down.


I thought for sure I erased network config so next step was to vi into /etc/network/interfaces to verify settings. Here comes the weird part... All my IP information is still in there?? So no idea why ETH0 all of the sudden is not reading info from this file?


I have pretty much Googled and tried everything in the book and still can't get any IP info for my ETHO to show up. 


Sorry for the lengthy explanation and I really hope someone can help me out as I am running out of ideas.

---

### Post by howefield on 2015-03-02
Thread moved to the "*Server Platforms*" forum.

---

