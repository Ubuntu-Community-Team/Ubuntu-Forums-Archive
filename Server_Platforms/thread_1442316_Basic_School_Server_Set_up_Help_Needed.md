---
title: "Basic School Server Set up Help Needed"
date: 2010-03-29
forum: Server Platforms
---

### Post by milton891 on 2010-03-29
Hi all, 
I am formally a student at a small collage in Pa and was asked to help them with there IT department that is really nonexistent.  I have not gone to school for IT but I am very tech savvy and have built and worked on computers in the past.

In the past few weeks I have gotten them off of their old satellite link (that was very slow and we always used too much bandwidth) and got a T1 installed.  I also got rid of their old home base router (the kind you would get off the shelf off wal-mart) that kept crashing and rebooting and installed a NetGear Pro Safe FVS336G router.

I need to set up a few things: 
1. A Server that will monitor the internet and filter when students can get to some websites (Facebook only in the evenings etc.).  As part of this I will need to set up classes of users with a default (for students) and a special (for staff) that will have different privileges.
2. A storage server (They currently have an old computer running Win Server 2000 with all their information on the same hard drive as the OS) this will need to be set up in a raid configuration. 
3. I also need to have something that i can log system status of the T1 as well as my WIFI points so i can check if things have gone down when i get complaints. 

There is about 20 staff computers most are hardwired but some are laptops and there are about 40 students most have laptops.  We have three wireless access points in two building that are connected with a fibber cable.

I need help with specs on what I would need hardware wise in the Server computer I want to build, and what kinds of programs I need to accomplish what I am trying to do (hopefully mostly freeware/Linux based stuff).

I am looking at a budget of about $2500 but that might be able to change a bit.  Mostly lower cost though.

Like I said earlier I have not gone to school for this so any help would be great.

---

### Post by Jakob Lundberg on 2010-03-30
Here are some software suggestions:
1. DansGuardian
[https://help.ubuntu.com/community/Servers/DansGuardian](https://help.ubuntu.com/community/Servers/DansGuardian)

2. Samba
[https://help.ubuntu.com/community/Samba/](https://help.ubuntu.com/community/Samba/)

3. Nagios 
[https://help.ubuntu.com/community/Nagios3](https://help.ubuntu.com/community/Nagios3)

---

### Post by Sporkman on 2010-03-30
If you need file serving with Apple computers, you can look at netatalk:

[http://packages.ubuntu.com/jaunty/netatalk](http://packages.ubuntu.com/jaunty/netatalk)

---

### Post by jrssystemsnet on 2010-03-30
Good lord - how small of a college IS this, that a single Netgear ProSafe (and a single T1!) is sufficient to drive the entire network?!

---

### Post by terazen on 2010-03-30
1.  Would a traffic shaper (like pfsense) work better?
3.  You could use jffnms or nagios internally and something like pingdom.com to monitor your T1.  I only suggest pingdom because that's what we use, but there are others I'm sure.  If you only have an internal nms then emails won't go out when the T1 is down (I'm partial to them coming in as texts directly to my cell phone).

---

### Post by adgators89 on 2010-03-30
I am interested in this post as well, I would like to add a web server to our existing school server(which is windows 2003 - but 5 years old).  I would like to use a seperate computer to do this a regular desktop 2.8ghz intel core2 -  2mb ram with 160gb hard drive.  Is this adequate to be a webserver and if possible a mail server as well?  This way I can eliminate the fees that we pay to a hosting company for the mail and site hosting that we currently use.  I would dedicate this computer to doing these tasks only so that it is not affected by other tasks.  Does anyone have any ideas on how I can do this? I saw the LAMP install, is that what I need to do?  and if so, how do I use my assigned internal ip address to configure the webserver?

---

### Post by terazen on 2010-03-30
> **adgators89 said:**
> I would like to use a seperate computer to do this a regular desktop 2.8ghz intel core2 -  2mb ram with 160gb hard drive.  Is this adequate to be a webserver and if possible a mail server as well?

1.  CMS websites that are heavy php can get cpu up pretty good with hundreds of people connected to it, but other than that those specs look like plenty unless you have a ton of folks hitting your servers constantly.

2.  You should go ahead and open a new thread. ;p

---

### Post by ICEB3AR on 2010-03-30
To The primary topic:
1. Depending on how the Users should have to be seperated maybe a Captive Portal software like CoovaChilli should be worth a look.
2. if there is only Linux/Mac on the network NFS should be nice.

---

### Post by milton891 on 2010-03-30
> **jrssystemsnet said:**
> Good lord - how small of a college IS this, that a single Netgear ProSafe (and a single T1!) is sufficient to drive the entire network?!
Thanks for all the comments.  The Netgear router is only at the top end it goes to switches from there to break out into the rest of the computers and WIFI access points.

---

### Post by milton891 on 2010-04-02
Hey another part of this i asked earlier and was wondering if i could get more info on is what kind of parts do i need in a server computer i know video card and stuff i really only need on board but should i put extra ram in it and if now what is ok on the ram end of stuff 1gb? Thanks.

---

### Post by Jakob Lundberg on 2010-04-02
The amount of ram you need depends on how many users you have. At 60 users any of the functions should be fine with 1gb. Hard to say with all 3 functions on the same server.

But upgrading should be fairly easy. If your budget only allows for 1 gb, you can start there and add more later.

---

