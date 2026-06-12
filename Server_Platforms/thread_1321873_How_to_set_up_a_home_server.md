---
title: "How to set up a home server?"
date: 2009-11-10
forum: Server Platforms
---

### Post by blur xc on 2009-11-10
I'm wanting to build a home server.  I also know next to nothing about servers.  I would like to to primarily be a file server, with a handful of drives in a raid 5, and after that I would like it as a gateway(?) running dansgaurdian to filter my kids' internet usage.  They are getting small laptops for Christmas so it's an issue my wife and I need to sort out. 

Is there some idiots guide, tutorial type instruction somewhere that can help me sort out what I need and how to do it?  I probably won't get to it for at least a few more months but I'd like to have as much figured out before I dive in and start buying stuff.

thanks,
BM

---

### Post by ali_williams on 2009-11-10
> **blur xc said:**
> I'm wanting to build a home server.  I also know next to nothing about servers.  I would like to to primarily be a file server, with a handful of drives in a raid 5, and after that I would like it as a gateway(?) running dansgaurdian to filter my kids' internet usage.  They are getting small laptops for Christmas so it's an issue my wife and I need to sort out. 

Is there some idiots guide, tutorial type instruction somewhere that can help me sort out what I need and how to do it?  I probably won't get to it for at least a few more months but I'd like to have as much figured out before I dive in and start buying stuff.

thanks,
BM

[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page) <- this site is great on showing you how to install the applications but as far as a step by step on how to create a server sorry thats all i got :D

---

### Post by BadBoy4Live on 2009-11-10
Try this link

[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver).

Its a manual on the basics for creating a fileserver

---

### Post by blur xc on 2009-11-10
Thanks!  Do I understand correctly that drives you want shared w/ a windows computer, via samba, have to be ntfs?

BM

---

### Post by volkswagner on 2009-11-10
> **blur xc said:**
> Thanks!  Do I understand correctly that drives you want shared w/ a windows computer, via samba, have to be ntfs?

BM

No.  Computers accessing the share do not read the file system.

---

### Post by Spiritof76 on 2009-11-10
> **blur xc said:**
> Thanks!  Do I understand correctly that drives you want shared w/ a windows computer, via samba, have to be ntfs?

BM

I believe that the tutorial assumes that you may at some point want to load the data drive onto a windows box. NTFS is a pretty universally read.  I figure I can always access it on another ubuntu box.

---

### Post by kewlrichie on 2009-11-11
Hey I would recommend adding some more keywords like proxy samba dansguardian in the thread title so someone like me who can help you out with proxy/web filter stuff can find It without me just going into a post with a generic title like home server help. I'm not trying to be a jerk just some friendly advise :) 

Anyways building a proxy with web filtering is not that much work and I would be gald to help if youneed any. I posted quick run through in another post over here [http://ubuntuforums.org/showthread.php?t=1317538]("http://ubuntuforums.org/showthread.php?t=1317538"). As I mentioned in that thread there is another guide on howtoforge that set it up slightly different using auto poxy detection etc..I chose to use the transparent proxy method I've been meaning to start making a how to guide myself but I've been busy...btw dansguardian is a great price of software and it is definitely what you are looking for and will work well..you can setup groups for let's say the kids and different group for your wife, Block by certain words/phrases, load huge blacklists by catagory, block certain file extensions/types from being downloaded and the ones that you allow can be scanned for viruses via clamav already built into the later version of dansguardian

Rich

---

