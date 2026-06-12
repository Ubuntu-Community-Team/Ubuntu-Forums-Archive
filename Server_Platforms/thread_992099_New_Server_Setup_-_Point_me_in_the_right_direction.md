---
title: "New Server Setup - Point me in the right direction"
date: 2008-11-24
forum: Server Platforms
---

### Post by CRMcMullen on 2008-11-24
Hello all ...

I've got lots of experience setting up desktops, now I want to set up my first production server.  Have practiced a couple times with setting up a simple LAMP server and I'm good with that.  

Now I've got a brand new Dell Dual Core Pentium E2180 server with 2GB of RAM and two 250GB SATA drives connected to an onboard SATA controller, no RAID option.  

My biggest question with the install is what's the best option for install with these hard drives?  This is a development server and I have enough backup storage to backup the entire machine ... so RAID (fakeraid?) isn't crucial.  I'd like this server to just be a utility machine (e.g. web  server, print server, file server).  

My first run at install created a "/dev/mapper/" that appears to be only recognizing 1 drive (or is it both drives in a fakeraid by default?).  Am thinking I need to enter some options at install time.

Now it's your turn.  What are your recommendations on install options?

Thanks in advance.
- Casey

---

### Post by koenn on 2008-11-24
> **CRMcMullen said:**
> 

My first run at install created a "/dev/mapper/" that appears to be only recognizing 1 drive (or is it both drives in a fakeraid by default?).  Am thinking I need to enter some options at install time.


you probably installed LVM, which is software that allows you to span disks to create logical volumes. You could check and see if the device in /dev/mapper/... is (almost) 500 GB in size.

You probably want a software raid - it's also an option during the install (mdadm)

---

### Post by CRMcMullen on 2008-11-24
Ok, I'm catching on here.  Yes I did install LVM, as I want both drives to appear as one 500gb drive.  I've got both drives now added to one LVM group, which appears as a single 500gb drive, but only the space of the first drive is allocated, none of the second.  No idea (yet) on how to get that accomplished, or if I've even installed and set it up correctly.

---

### Post by koenn on 2008-11-24
> Yes I did install LVM, as I want both drives to appear as one 500gb drive
OK, then you do want lvm, not raid

I don't quite understand what you mean by 
"I've got both drives now added to one LVM group, which appears as a single 500gb drive, but only the space of the first drive is allocated, none of the second." How can you have a 500 GB volume if only one if your 250 GB disks is used ?

Anyway, you may still need to create the actual logical volumes (LV's) - with lvcreate.
This will get you in the right direction :
[http://users.telenet.be/mydotcom/howto/linux/disks2.htm](http://users.telenet.be/mydotcom/howto/linux/disks2.htm)

---

