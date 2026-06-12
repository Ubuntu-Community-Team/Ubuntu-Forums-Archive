---
title: "Installing on HP DL380 G7 with (hardware) RAID 1+0?"
date: 2011-07-20
forum: Server Platforms
---

### Post by mnwolftrack on 2011-07-20
Hello--I'm new to Ubuntu Server (just downloaded 11.04).  I am installing it on a new HP DL380 G7 that I set up with six 72GB 15k RPM SAS hard drives with RAID 1+0 using the built in HP hardware array controller P410i (I think).  I am not sure if Ubuntu is seeing the array correctly, though it may be.  When I get to the installation step of of the Ubuntu install where it wants to partition the drive(s), it appears to bring up the array as:

SCSI3 (0,0,1) (sda) - 220.1GB HP Logical VOLUME.  

I'm not quite following this information or if it is seeing all 6 hard drives as one (as with RAID 1+0).  Any help would be appreciated.  Normally, the total hard drive size with six 72GB drives should be about 205GB, so I'm not sure where the 220.1GB is coming from.  

All I want is for the hardware to manage the raid and just partition one big volume.  Also, one of the Ubuntu installation options was to partition and install LVM--I don't know if I need LVM when I just have the one partition???

---

### Post by mnwolftrack on 2011-07-20
Wow--I feel really stupid and overwhelmed (but determined).  I've only just started using any form of Linux for a whole 4 hours now, having come from and managed Windows clients and servers all of my previous computing life.  I just realized all of my Windows experience means nothing in helping me figure out Ubuntu Server 11.04.  

A little update--I installed Ubu 11.04 using the "guided" partitioning setup with VLM and basically just let it use all it's defaults.  So, I seem to have a working version of 11.04, but I have no idea how to tell if I really have RAID 10 working or not (my original question).  And I'm almost too afraid to admit I was expecting a GUI interface!  I wasn't expecting a Windows clone by any means, but wow is this different!  (not BAD, just very different!).  

If I learned anything today in my 4 hours of experience with Linux, is that my learning curve just got a lot longer.   My pipe dream of figuring this thing out and having a file server up and running in a day or so are gone.  That being said, I am determined to figure this out.  I am tired of the Windows world.

---

### Post by mnwolftrack on 2011-07-21
Is my question too specific and unusual, too stupid, etc??? I know Windows very well--which means it's going to likely be extra hard for me to UNLEARN everything I thought I knew.   Just looking for some guidance to verify if I really have my drives set up as RAID 10. I did a search and found references to setting up software RAID 1 or 0 or 5, but not 10, and much of what I found was regarding Ubuntu 10.x or older (and I downloaded 11.04).

---

### Post by nothingspecial on 2011-07-22
Some reading

[http://www.howtoforge.com/install-ubuntu-with-software-raid-10](http://www.howtoforge.com/install-ubuntu-with-software-raid-10)
[http://symbolik.wordpress.com/2009/05/01/howto-kubuntu-904-raid-10-lvm2-and-xfs/](http://symbolik.wordpress.com/2009/05/01/howto-kubuntu-904-raid-10-lvm2-and-xfs/)

useful info in the comments

---

### Post by The Cog on 2011-07-23
> **mnwolftrack said:**
> HP DL380 G7 ... six 72GB 15k RPM SAS hard drives with RAID 1+0 

SCSI3 (0,0,1) (sda) - 220.1GB HP Logical VOLUME.  

Normally, the total hard drive size with six 72GB drives should be about 205GB, so I'm not sure where the 220.1GB is coming from.  

All I want is for the hardware to manage the raid and just partition one big volume.  Also, one of the Ubuntu installation options was to partition and install LVM--I don't know if I need LVM when I just have the one partition???
The DL series use the hardware raid to emulate one large disk. The one large disk is all that Linux sees. Ignore the 220/205 difference - it is probably a difference in opinion over the size of a gigabyte - 10^9 or 2^30.

Don't worry about LLVM - logical disk management. Just use the disk as one large disk. Its name is sda - (scsi disk a). 
You could just let the installer use the entire disk, but then you have problems next time you want to install the next version of OS. So if this is a temporary install just for learning I would go for a whole-disk install because it's easiest. For production, I would suggest that you manually create 4 partitions (advanced partitioning):
sda1 10G ext4 mounted as "/"
sda2 10G ext4 unused
sda3 2G swap mount as "swap" virtual memory
sda4 the rest, ext4, mounted as "/home" for user data.
10G is possibly over-generous for the system, but you won't run out. 2G for swap (virtual memory) is debatable and flexible.
The unused partition can be used to install and test the next version of OS on later, leaving your user data and previous version there as a back-out option.

I have only played with samba once, and would note that it wasn't immediately obvious from the documentation that I saw that samba maintains its own user/password database independent from the OS one. It took me an age to figure out why users were being told bad password. So keep an eye out for that little gotcha.

You are probably better off installing the desktop version of Ubuntu. I see you have discovered that the server edition is GUI-less, which can be rather hard-core for a newcomer. Installing the desktop version will install a bunch of stuff that you don't need as well, but won't affect performance too much and will make finding your way round a lot easier. The server version has a kernel optimised for server type workloads, but I don't think the difference is all that huge. Maybe you should install ubuntu-desktop over the server version, **sudo apt-get install ubuntu-desktop** should do it.

I saw your comments about Ubuntu being completely different and having to unlearn things. This is true. The problem you have is that many concepts remain the same while others are completely different, and at the moment you don't even know which ones you will have to un-learn. Drive letters (absence of) is an early example.

Good luck. Use these forums, specific questions generally get very good answers.

---

### Post by koenn on 2011-07-23
The fact that your seeing 1 220 GB "HP volume" from 6x72GB disks in raid 10 is good. It's a clear indication Ubuntu has recognized the HP raidcontroller. I agree with The Cog that the difference is most likely a matter of disagreement about how big a gigabyte is supposed to be. 


re
> Is my question too specific and unusual, too stupid, etc??
be patient. This is volunteer support. You want an SLA, Canonical will be happy to sell them to you. 

About hardware raid controllers - the operating system (be it Windows or Linux, or anything else) only shows the OS "volumes" a,d makes abstraction of the actual disks. You configure that in the controller's SETUP program, which you can usually access during the hardwate boot (~BIOS). This is NOT a feature of the operating system.
HP does, however, have some tools that can help you manage additional disks or arrays after the operating system is loaded. They exist for Windows, I don't know if HP also makes them for linux. 
In any case, the raid setup program issifficient to set up the raid level and LUNs you need. 
If the above confuses you, remember what I said in that other thread, about "knowing how to accomplish a task using 1 specific tool" vs "knowing what your doing and being able to do it with any suitable tool" :-)


Also; beware of pointers to howto's about software raid. You don't want that, you already have a raid. 


Re partitioning : you're going to need space for files, because your building a file server. Dedicate a partiotion to it, and make it large enough. mount it on /srv and configure samba to share out /srv or subdirectories of it. 
You may or may not need a partition for /home, depends on your plan. 
Other than that, i find The Cog's partition not unreasonable.

In stead of partitioning (i.e. at filesystem level), you might want your raid controller to present seperate LUNs for those partition (think "disks", but not the 6 actual physical disks, but chunks of the array, which the raid controller presents as disks to the OS).
Aigain, it's your raid controllers setup program that handles this, not Ubuntu : Ubuntu only says the result : storage that can be used to build a filesystem on. 



So far, your questions have little to do with Ubuntu, and a lot with understanding your hardware. But that too is part of setting up a server, so you get away with it :-)

---

### Post by kgatan on 2011-07-25
I dont know if your just messing around with the server or trying to make something serious but note that its recommended to use Ubuntu 10.04 LTS for server use.

LTS "Long Time Support" means that that specific version will receive updates much longer then ordinary versions.

Normal = 18 months
LTS = 5 years

---

### Post by leftcase on 2011-10-12
I know this is an old thread, but just to point out, you can install the HP Array Configuration Utility onto Ubuntu to monitor and control RAID from the Operating System. You'd probably want to couple this with a notification system to let you know of drive failure.

[http://pyarra.blogspot.com/2011/03/ubuntu-server-on-hp-proliant-managing.html](http://pyarra.blogspot.com/2011/03/ubuntu-server-on-hp-proliant-managing.html)

---

