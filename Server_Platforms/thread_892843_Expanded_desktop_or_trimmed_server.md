---
title: "Expanded desktop or trimmed server?"
date: 2008-08-17
forum: Server Platforms
---

### Post by lnoland on 2008-08-17
Hi.  I am hoping that I can get some advice.  I recently purchased a new machine for my home network.  I had some specific ideas in mind when I purchased it but now I am not so sure.  My plan was to set up a server for my home computers (three or four Windows-based machines for which I am generally the only user).  I have been getting interested in virtualization (and portability) recently so my plan included, in addition to using the new machine for a server, running various desktop OS's (including Ubuntu desktop and Windows Vista Ultimate) in virtual machines -- I would primarily be running them directly on the server so I would need to install a windowed environment.  For this task, I purchased an Intel Quad core machine with 8GB of memory so I figured I would have plenty of horsepower for this shared duty.

My plan was to use Ubuntu Server as the base OS.  It seems like a very attractive and well thought out distribution.  My needs are relatively modest.  I want to run Samba so that I can provide file and print sharing for my Windows computers.  I thought I might try using it as a domain controller as well so that I can more easily manage my multiple machines, have uniform authentication, etc.  Having a network-based Backup solution is something I am very interested in, even if I have to bastardize things a bit to make it work for disaster-recovery on both my Linux and Windows systems (I figure on the Windows systems, I am going to need to do some sort of Windows-based backup to capture the current system state and then use the network backup to backup the resulting backup files (along with the rest of the Windows files) to whatever backup medium I settle on for the network.  At some point I might wish to look into setting up OpenVPN to allow for secure external operation (e.g. if I am on the road) but I have no current plans.  I might consider running an imap mail server (again, down the road) primarily as a mail aggregator (since I'm the only user, it seems like overkill, but managing access to my various email accounts is currently a problem).  Originally I thought I might use KVM for running my virtual machines, but after spending a lot of time reading about it, I think I would probably be better off with VMWare desktop or possibly VirtualBox.  I don't foresee myself setting up a web server, connecting to a Windows domain, managing a bunch of users, etc.  I would, however, like to look into adding a MythTV package to the mix.

I should add that I will be a newbie not just to Linux but to server environments as well.  I have been working as a software engineer for over 30 years and a few of those years were on a Unix Platform (but not ***for*** a Unix platform) so I am not completely unfamiliar with the *nix environment (I'm pretty fluent in Korn Shell programming and VI and also use the MKS Toolkit at work) but I have never had root access before so I have no admin experience.

As I read through Ubuntu server documentation, the forums, etc. I have come to question if I am on the right path for my goals.  Perhaps I should be installing Ubuntu desktop and fleshing it out with the Packages I need to accomplish my server needs.  I have a feeling that if I were to go that route I would probably be less inclined to suffer at the hands of my own ignorance since I suspect that the desktop distribution probably has fewre pitfalls for the newbie to fall into (though I realize that once I start installing Server-level packages, like Samba, I start uncovering new pitfalls).

What do you all think?  Is my original plan a bad idea?  Is my alternative plan any better?  Any comments or suggestions you can make I would very much appreciate.  Thanks.

 - Les

---

### Post by cariboo on 2008-08-17
I think the desktop sytem would be the best for what you are planning.

Jim

---

### Post by lnoland on 2008-08-17
> **cariboo907 said:**
> I think the desktop sytem would be the best for what you are planning.

Jim
Thanks for the reply.  Do you have a specific reason for recommending the desktop or is that just an instinctive judgment?  Do you think I would be better off working with it as just a desktop system for awhile and learn the ropes a bit before say, trying to setup some of the server functions or should I dive right in (keeping in mind that, since all my other machines are Windows, a Linux system without any file-sharing set up will probably limit what I can do with the system prety severely since I would be somewhat isolated).

 - Les

---

### Post by thefekete on 2008-08-18
My advice would be to set up a desktop environment and spend some time getting used to the environment. 

The first thing you should do is set up virtualization (I prefer VBox for simplicity, and licencing). That way, you can set up various servers and experiment with the various services and their "pitfalls" before running them on your main system.

The only difficult part in getting virtualization running is giving your machines their own IP on your network (host networking or bridged networking). This seemed really complicated for me at first, but I decided to give it a go last week and it wasn't as bad as I had thought (YMMV). Here's the howto for virtualbox on ubuntu:
[https://help.ubuntu.com/community/VirtualBox#Networking]("https://help.ubuntu.com/community/VirtualBox#Networking")

Samba is really easy to set up, there's a ton of howto's on the intertubes. The easiest way to set that up is to enable users homes to be exported. This makes any user's home directory on your system automatically available on the network. Samba is also the easiest way to perform backups on windows systems in conjunction with something like [Allway Sync]("http://allwaysync.com/"). rsync and cron is the way to go with other linux systems.

I'd also recommend setting up an ssh server (super easy, just apt-get openssh-server) and installing Putty on your windows machines to allow remote administration without having to walk across the room/house.

The more you poke around, the more you'll find that you want a different setup. I probably reinstalled about 10 times on my home server before I got it how I wanted.

Just dive in and keep external backups. But most importantly, document everything you do. Use a blog or a wiki or a notebook, just make sure you record what you added and what you changed. This is invaluable for when you decide to start over and you can't remember how you set up samba or apache to work exactly how you wanted.

There are two books I highly recommend, the first is [How Linux Works: What Every Super User Should Know]("http://www.amazon.com/How-Linux-Works-Brian-Ward/dp/1593270356/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1219050797&sr=1-1") by Brian Ward. It's a great starter for running linux as a server or a desktop. It's a great general reference for basic rootly powers. When you're ready to start digging into serious admin stuff, go with [Linux Administration Handbook (2nd Edition)]("http://www.amazon.com/Linux-Administration-Handbook-2nd-Nemeth/dp/0131480049") by  Evi Nemeth, Garth Snyder and Trent R. Hein. It covers just about anything you need to know about administering linux servers and networks. I owe much of what I know to these two great resources.

Anyways, good luck and have fun.


-dan

---

### Post by lnoland on 2008-08-20
> **thefekete said:**
> My advice would be to set up a desktop environment and spend some time getting used to the environment. 

The first thing you should do is set up virtualization (I prefer VBox for simplicity, and licencing). That way, you can set up various servers and experiment with the various services and their "pitfalls" before running them on your main system.

The only difficult part in getting virtualization running is giving your machines their own IP on your network (host networking or bridged networking). This seemed really complicated for me at first, but I decided to give it a go last week and it wasn't as bad as I had thought (YMMV). Here's the howto for virtualbox on ubuntu:
[https://help.ubuntu.com/community/VirtualBox#Networking]("https://help.ubuntu.com/community/VirtualBox#Networking")

I have been playing around with VirutalBox under Windows for a few weeks now.  I had to do some experimenting with the networking at first but eventually I got it all worked out.  I really like its speed and small-size (and its price) but was disappointed that one of the features I liked best (its built-in remote-desktop protocol) seemed too buggy to use and (at least under Windows) didn't seem to offer the remote-USB feature as advertised.  I was also bummed-out that it doesn't allow for what VMWare refers to as "Linked clones" (similar to Virtual PC's differencing disks).  Still, for the price, I will happily make use of it where I can.

> **thefekete said:**
> 
Samba is really easy to set up, there's a ton of howto's on the intertubes. The easiest way to set that up is to enable users homes to be exported. This makes any user's home directory on your system automatically available on the network. Samba is also the easiest way to perform backups on windows systems in conjunction with something like [Allway Sync]("http://allwaysync.com/"). rsync and cron is the way to go with other linux systems.
Thanks for the Samba-tip.  That sounds like it should get things rolling pretty easily.  Thanks, especially for the link to "Allway Sync" -- I have been looking for something like this for a long time but most things I have tried have disappointed -- the customer endorsements make this sound like something I should definitely check out (and again, the price is hard to beat).
> **thefekete said:**
> 
I'd also recommend setting up an ssh server (super easy, just apt-get openssh-server) and installing Putty on your windows machines to allow remote administration without having to walk across the room/house.
I have also seen references to something called VNC which I gather is something like Windows "Remote Desktop".  I presume the main difference here is that SSH is for remote command shell work and VNC yields remote GUI access. Correct?
> **thefekete said:**
> 
The more you poke around, the more you'll find that you want a different setup. I probably reinstalled about 10 times on my home server before I got it how I wanted.

Just dive in and keep external backups. But most importantly, document everything you do. Use a blog or a wiki or a notebook, just make sure you record what you added and what you changed. This is invaluable for when you decide to start over and you can't remember how you set up samba or apache to work exactly how you wanted.
Sounds like great advice.  I have often wished, in the past, that I had kept logs regarding changes I have made to my systems.  I tried once or twice but never kept at it -- usually, after some late-night session where I'd made a few dozen different changes in an attempt to get something working I'd realize that I had no idea what all I had changed and would just give up on the idea.  I think I need to find a more systematic approach (or maybe even apply some automation of some sort to track what I'm doing so I can document it later).  Of course, in Windows, it seems next to impossible to ever set things up the same way twice -- there are so many "automatic updates", behind-the-scene setting changes, etc. that there seems to be little hope of ever retracing one's steps.
> **thefekete said:**
> 
There are two books I highly recommend, the first is [How Linux Works: What Every Super User Should Know]("http://www.amazon.com/How-Linux-Works-Brian-Ward/dp/1593270356/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1219050797&sr=1-1") by Brian Ward. It's a great starter for running linux as a server or a desktop. It's a great general reference for basic rootly powers. When you're ready to start digging into serious admin stuff, go with [Linux Administration Handbook (2nd Edition)]("http://www.amazon.com/Linux-Administration-Handbook-2nd-Nemeth/dp/0131480049") by  Evi Nemeth, Garth Snyder and Trent R. Hein. It covers just about anything you need to know about administering linux servers and networks. I owe much of what I know to these two great resources.

Anyways, good luck and have fun.

-dan
Thansk so much for all of your help and advice.  There's lots of information available but it can be hard to see the forest for the trees.  It is really helpful to be able to take advantage of the trail someone else has blazed.

---

