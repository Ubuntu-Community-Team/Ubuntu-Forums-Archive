---
title: "Ubuntu Server plus Dell PowerEdge R510 -- Yes?"
date: 2010-07-12
forum: Server Platforms
---

### Post by lykwydchykyn on 2010-07-12
I need to recommend hardware for use with an LTSP 5 setup running on Ubuntu Server 10.04.  Since we have contracts with Dell, I need to recommend a Dell server.  Is anyone using the R510 with Ubuntu, and if so have you had any compatibility problems?

---

### Post by ruffEdgz on 2010-07-12
I can't say that an R510 works well with Ubuntu 10.04 but I can say the R710 works well.

I just installed Ubuntu 10.04 (64 bit) onto a Dell R710 with these specs:

HDD = 6 x 146GB RAID 5 
MEM = 24GB
CPU = Intel(R) Xeon(R) CPU X5670 @ 2.93GHz

I kickstarted it, made my changes and so far, everything that is installed is working like it should. I installed it with the 'ubuntu-minimal' package and then installed some additional packages when I was able to log in.

I hope this helps but if you need me to give you any other specs from the R710, please let me know.

---

### Post by lykwydchykyn on 2010-07-12
Thanks, that's good info.  I'll have to compare and see if anything significant is different between the two.

---

### Post by hierophant on 2010-07-14
I have an R710 running Windows Server 2008 x64 Standard.  It boots from RAID1 on bays 0-1 of the SAS 6i, with several logical volumes on an MD3000.  I primarily use it for data analysis with SQL Server.

I'm not using it much currently, and I'd like to play with Ubuntu 10.04 Server.  I recently installed it on an old gaming box, and am very impressed.

Is there a way to do that without trashing my Windows installation?

Two approaches come to mind, and I can see problems with both.  I could add two small SAS drives in bays 2-3, and install Ubuntu on them.  However, Ubuntu might mess with the Windows boot drives, and trash the installation.

Alternatively, I could pull the current boot drives, and add two small SAS drives for Ubuntu.  However, SAS 6i stores the RAID setup in its BIOS, and would be very confused.

When taking either approach, and booting into Ubuntu, I wouldn't power up the MD3000.


Is this just a bad idea?

---

### Post by lykwydchykyn on 2010-07-27
Ok, update for those considering this server:

 - DO NOT GET THE DEFAULT PERC S300 RAID CONTROLLER

It does not work with Linux.  Period.  Windows Only (I have this from tech support).  So now I'm waiting for my SAS 6ir controller, maybe...

I thought we were past this windows-only junk (at least in the server room)?

---

### Post by ruffEdgz on 2010-07-27
Wow, I didn't know they had RAID controllers for 'Windows' only. In that case, I will place in this post the type of RAID controller I'm using as it didn't have any issues when I got it (for the record that is):

* PERC 6/i SAS RAID Controller, 2x4 Connectors, Internal, PCIe, 256MB Cache

Sorry that you had to deal with that part but now we know not to get that type of PERC S300 RAID Controller.

Outside from that, I don't see why anything else wouldn't work for a Dell R Series Server. Thanks for the update.

---

### Post by lykwydchykyn on 2010-07-27
> **ruffEdgz said:**
> Wow, I didn't know they had RAID controllers for 'Windows' only. In that case, I will place in this post the type of RAID controller I'm using as it didn't have any issues when I got it (for the record that is):

* PERC 6/i SAS RAID Controller, 2x4 Connectors, Internal, PCIe, 256MB Cache

Sorry that you had to deal with that part but now we know not to get that type of PERC S300 RAID Controller.

Outside from that, I don't see why anything else wouldn't work for a Dell R Series Server. Thanks for the update.

Fortunately our sales rep was classy enough to send us the 6/i as a free replacement.  Still frustrating.

The PERC S300 is a "software raid controller", which means part of the RAID logic is actually handled in software loaded to the OS.  And that software is... you guessed it.  Windows Only.

It just frustrates me that this was not made clear on the site, especially since I ordered a server with no OS. It oughta ship standard with the most compatible controller, but then I don't understand marketing.

---

### Post by lykwydchykyn on 2010-07-30
ARRRRGHHHHHHH!!!!!!!!!!!!

Another caveat:  the SAS 6/ir or whatever this garbage they sent me is called **doesn't do RAID 5**.  I'm really disappointed by this, since past iterations of the PowerEdge line worked splendidly with Linux, now I have to put up with this crud.

Excuse me while I bang my head into the wall and contemplate a phone call to HP.

---

### Post by ruffEdgz on 2010-07-30
I'm sorry man that you are having issues with Dell right now. Here is a list of what PERC cards can do for you.

[http://www.dell.com/content/topics/topic.aspx/global/products/pvaul/topics/en/us/raid_controller?c=us&l=en&cs=555](http://www.dell.com/content/topics/topic.aspx/global/products/pvaul/topics/en/us/raid_controller?c=us&l=en&cs=555)

I know this doesn't solve your issue but I want to make sure the info is out there. I don't use Ubuntu on any production servers right now (in the process of talking with [Canonical](http://www.canonical.com/) right now to see how we can move away from Red Hat. One of those issues is the Dell Support.

I really am sorry to hear about the problems you are having but the actual installation of Ubuntu on a new Dell R Series server does work. So if you want to stay with Dell, it can be beneficial.

---

### Post by lykwydchykyn on 2010-07-30
Fortunately our sales rep is a real class act, so he's got some people looking into getting me a card that will do what I need.

I'm just disappointed that in 2010 they're going to ship a RAID controller that requires Windows, then recommend a replacement that has far less capability.

---

### Post by ruffEdgz on 2010-07-30
I totally understand what you are saying. I noticed that Dell has changed a lot from their PE series to these R series models but it might have been for the best at least in my opinion.

I noticed that I have more choices in the R series then before (granted, I sometimes have to ask more questions but the choices are there). With those new choices, I was able to get what I wanted but at an affordable price.

It hasn't always been 'sunshines and rainbows' with Dell and their Reps/Support but I do love their servers and the quality that comes with them after getting through the loops ;)

---

