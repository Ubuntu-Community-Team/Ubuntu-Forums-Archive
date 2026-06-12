---
title: "Setting up Server 12.10 on Proliant ML370 G3 (Help Apreciated)"
date: 2013-01-22
forum: Server Platforms
---

### Post by WalterTScott on 2013-01-22
My First time Posting on Ubuntu Forums. Iv'e found it very helpfull in learning alot about Ubunt, (and linux in general.) However I am now at a point i need some coaching to get the most out of this old system. Thanks to all in advance.
 
What i have is an older PRoliant ML370 G3 rack server, with 4 GB of ram and 2 Xenon processors running at 3Ghz. A x64 IDE SCSI RAID Controller running 6 36Gb Ultra 360 hard drives. The system also has ILo for remote administration.
 
I may have some of the details above a little wrong as i have locked up the garage for the night and am going off memory, ( I need a few more Gigs i think ;).) I will update with more detail tomorrow as i will be reinstalling everything again, again.
 
So far i have been able to somwhat succsefully install Ubuntu server 12.10, i had a lot of problem with the RAID but was able to get it to boot, finaly, using supergrub to correct the grub boot loader after install. I have not yet been able to get it to boot from the IDE hard drive. But it does boot from the IDE CD ROM, frustratingly on the same cable as the IDE hard drive.
 
NB: I had to install Ubuntu Server 8.04 CD then upgrade till i arrived at 12.10. I could not install it from any later version of the CD.
 
every thing seems to run well under 12.10 however i have not yet figured out how to mount and navigate the hard drives.
 
I then attempted to install a GUI. XUbuntu-Desktop,( I did this as i needed to access the floppy drive to do a BIOS upgrade on a diffrent system that is currently down.)
 
The system now attempts to start xubuntu 12.10 and hangs after the loading screen, then shuts down the monitor. I attemted boot ubuntu server 12.10 recovery from GRUB and can see that the video or monitor fails when loading. I suspect the problem has somthing to do with this.
 
However Ubuntu Server 12.10 wont load. instead showing an error. " /dev/md0 does not exist ," and drops to a buisybox shell.
 
If anyone is familiar with my problem, your advice might save me alot of time, however at the moment i plan to reinstall the system tomorrow. I will post everything i do with as much detail as possible as i have not found very much on here about my specific problems. Hopfully others will be able to learn more too.
 
P.S. I am new here so if i have posted this in the wrong area please point me to where i should post it and i will attempt to move it thanks.

---

### Post by Bucky Ball on 2013-01-22
*Thread moved to **Server Platforms***

Welcome to the forums. You might have more luck here.

---

### Post by WalterTScott on 2013-01-22
> **Bucky Ball said:**
> *Thread moved to **Server Platforms***

Welcome to the forums. You might have more luck here.
Thanks Mate, Appreciate that

---

### Post by chrisguk on 2013-01-22
Hi and welcome to the forums.

In general no matter what your hardware is the setup of Ubuntu server is the same in that the questions on boot are the same depending on your requirements.

To start I would take a look at this guide to give you a feel for the system:

[https://help.ubuntu.com/12.04/serverguide/]("https://help.ubuntu.com/12.04/serverguide/")

Its a great resource to any basic question that you may have.

Questions you need to answer prior to your installation:

1.  What do you want to use your server for?
2.  What services do you want to run?

Another guide I recommend is in the link below.  It started me off and its still pretty much current regardless of the Ubuntu version described in the guide:

[http://ubuntuforums.org/showthread.php?t=1895084]("http://ubuntuforums.org/showthread.php?t=1895084")

There are a lot of experts that frequent these forums and they will give you great advice, but most importantly "Google" is your friend and thats my first port'o'call for any questions that I may have.

With regards to your machine hardware.  Make sure you configure the correct RAID option before installing anything.  From what you have described you could run RAID 5 easy which I recommend.

Good luck and welcome to the world of Ubuntu ):P:popcorn:

---

