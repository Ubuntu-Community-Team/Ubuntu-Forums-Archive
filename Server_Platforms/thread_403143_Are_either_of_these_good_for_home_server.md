---
title: "Are either of these good for home server?"
date: 2007-04-06
forum: Server Platforms
---

### Post by Compucore on 2007-04-06
Hi Everyone,

WHere I am currently working they are tossing out two servers that are no longer being used in the shop and been already replaced with newer equipment. They have no more use for their law firm. I was wondering if either of them are good for home use or coud be used for something specific for home use. Here are the spec for both of them and what I want to do is to use Ubuntu dapper drake 6.06 LTS CD to install ubuntu on both and get Oracle 10g developer for free from Oracle through their web site to do some programming as a oracle developer. and maybe a web page server too. 

**Machine #1:**
Compaq Proliant ML370 G1
Dual Intel PIII 800 MHZ
Raid 5 with 4 SCSI 3 wide 18.2 gigabyte hard drives
1.5 gigabyte Ram
10/100 eithernet card
gigabit eithernet card
4U rack mount

**Machine #2:**
IBM E server 8669 4RX
Single PIII 1.266GHZ processor
Raid 5 with 4 SCSI 3 wide 18.2 gigabyte hard drive
10/100 etihernet
gigabit eithernet card
256 megabyte of ram
4U rackmount

They both have standard video cards which are okay for servers. They are not going to be used for gaming wish they could bu the machines are loud because of the fans running through them when they are powered up. Anyways I was thinking of used the compaq ML370 as a home oracle server and keep up with learning to program with Oracle 10 G developer edition (otn.oracle.com) which I could keep on the Compaq. While the other one I was thinking of making a webserver or using a program called Synchronet BBS which can be web capable with this machine and looks like a web page or using ssh or telnet programs that are still available for both ubuntu and windows environment. ([http://www.synchro.net/](http://www.synchro.net/)) 

The other thing that comes to mind as well for me what I wuold like to do as well and be able to do. Is there a software package that is capable of doing a three way conference between three or more machines. By example lets say that I am doing a conference between me and my younger brother. And what I want to do is to do a third conference to my 10G server and open the desktop automatically to the server. is there such an aplpication to do that. The only one that I can think of is VNC to do a virtual connection to see the desktop. But what I am looking for is to be able to open a desktop view and still be in a conference showing the results not only to me. But they can see it as well at the same time. Maybe even stream audio or type messags between use during the session. Any thoughts about this?

Compucore

---

### Post by jpkotta on 2007-04-06
I'm running a file/sftp server on a Gateway of unknown model.  It has a P3 @ 1 GHz, 256 MB RAM, and 10/100 D-Link RTL8139 NIC.  I have 3 250 GB Western Digital HDs and a Promise SATA controller running in a software RAID 5.  It has given me zero problems after I disabled the wireless card (I had no extra ethernet ports on the router when I first got it).  It also runs folding@home.  I should think you will have no trouble as long as your hardware supports Linux.  I would think about maybe getting some bigger HDs.  I'm using Dapper Server, but if you want a GUI, maybe try Xubuntu.

For your conference thing, I know that x11vnc can be used to attach to a currently running X server, but I'm not sure if two clients can attach to the same server.

---

### Post by Compucore on 2007-04-06
Hi jpkotta;2413413 I know for sure the compaq ML370 can use a couple of different variety of Linux, like rED HAT, sco Unix and I think one other one. Besides he windows bloatware of servers side too. Just a matter of getting it here and setting it up. The SCSI 3 Ultra I will plan to upgrade later on. Right now these are free and I just ned to get them set up in a way that they can be useful here. I'd rather stay with SCSI on these two servers that I have here. Not to put SATA down either. If the machine that I am bringing over here were capabale I would. But they are not so Gotta work within the limits of the technology it can use. The thing that I am debating as well over here. I know these two machines each have a 10/100 and a gigabit eithernet cards in them. Using the 64 bit  slots in each machine. Each has one of each so there is basically two nic cards in there. I'm just wondering if it is worth hooking them through in the gigabit to my small lan here. Or leave it on the 10/100 since the small lan that I am running is also a 10/100. And I know I might not see a difference between the two when its at 10/100. I would like to eventually get a gigabit hub or switch over here so I could take adavantage for the servers for moving files along. I know the 10/100 works great with little problem for general transfer from one pc to another.  Or just tie the two gigabit and use it to transfer what ever I need with a cross over cable between the two privately. 

Well that is what I am kind of looking for over here. What I would like to do is to have two clinets logged into the machine both seeing the same same thing on the screen and work with it that way. I know on the windows machine up to windows XP they had netmeeting where you could do that on two windows based machines.. I do not think that  Gain has the feature unti dapper drake. Since it will be accessed via another OS that is not linux. I nkow for sure once I get it set up there are some local terminal server under linux. but can't do the thing that I need to do. Like a meeting then a link to the server. But I know you understand of what I am looking for though. Just a mater of time to find out how to do the three at the same time. 

Compucore


> **jpkotta said:**
> I'm running a file/sftp server on a Gateway of unknown model.  It has a P3 @ 1 GHz, 256 MB RAM, and 10/100 D-Link RTL8139 NIC.  I have 3 250 GB Western Digital HDs and a Promise SATA controller running in a software RAID 5.  It has given me zero problems after I disabled the wireless card (I had no extra ethernet ports on the router when I first got it).  It also runs folding@home.  I should think you will have no trouble as long as your hardware supports Linux.  I would think about maybe getting some bigger HDs.  I'm using Dapper Server, but if you want a GUI, maybe try Xubuntu.

For your conference thing, I know that x11vnc can be used to attach to a currently running X server, but I'm not sure if two clients can attach to the same server.

---

### Post by krunge on 2007-04-06
> For your conference thing, I know that x11vnc can be used to attach to a currently running X server, but I'm not sure if two clients can attach to the same server.

Yes, just be sure to use the -shared option:

```
x11vnc -shared ...
```

---

### Post by elst on 2007-04-07
FWIW, Oracle offer Ubuntu-compatible packages for the XE edition of 10g, and these work very nicely: the only prerequisites are 1Gb swap (!), and the libaio1 package. I've just loaded this on Dapper, and it was the simplest Oracle installation I've ever done...

---

### Post by Compucore on 2007-04-07
I've used 10G express myself a little bit on the windows side to get more familar with it as well. That is why I was thinking of the regular 10g that you could download and install on a system. And I figured that the proliant that I will be brining home soon. WHich is more likely next weekend once I can get those tapes wiped first. And install it on this machine as a development machine for personal use and get more familar with it at the same time. Since there is a client side as well that can be installed so you can interface with it. And since this system will be using ubuntu linux Dapper drake 6.06 LTS. I figured it would be a good marriage of the two. And I could siimply interface it with the other machines via the client once I get everything set up. They are all going to be in the same room anyways. And instead of moving chairs left to right and back again. It would be a good way of learning more of Ubuntu and doing things like this for more experience on things. So far I prefer the 10G express over the previous like 8i or 9i. Especially when I was running them on a PII 233 and only 384 megs of RAM. Trust me it was looking at a catipillar walking ever so slowly. 

Besides it gives me more experence as well having something like this at home. ANd more training the better I always say.

Compucore

> **elst said:**
> FWIW, Oracle offer Ubuntu-compatible packages for the XE edition of 10g, and these work very nicely: the only prerequisites are 1Gb swap (!), and the libaio1 package. I've just loaded this on Dapper, and it was the simplest Oracle installation I've ever done...

---

