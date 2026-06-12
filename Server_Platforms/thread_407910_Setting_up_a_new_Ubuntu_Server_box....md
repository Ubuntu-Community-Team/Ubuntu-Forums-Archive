---
title: "Setting up a new Ubuntu Server box..."
date: 2007-04-12
forum: Server Platforms
---

### Post by dcastellani on 2007-04-12
OK so I have a Dual Xeon (Not dual core, two way xeon) dell box sitting at work. I want to use it as a syslog/svn/php/mysql/apache box for all sorts of IT projects I have cooked up at work.

Specs are as follows:
2 x 2.2 Ghz Xeon
4x 256 DDR PC3200 (1GB Total)
1x AGP
2x PCI 32bit
2x PCI-X 64bit
0x SATA PORTS of any kind


2x 500GB SATA2 (3G) harddrives

I want to use a real hardware raid controller, not a fakeraid, or software raid.  I just cant seem to find a compatible controller.  Ive heard 3ware and Highpoint both make controllers that are natively supported by Ubuntu 6.10 Server, but I am asking for some hard info.  What are some controllers that work natively with Ubuntu 6.10 Server.  I had a Promise TX2300 fakeraid 2port raid controller card laying around but that doesn't seem to natively work.  Are there other methods to have true hardware raid?  I know I could get SATA to IDE converters and just do software raid, but these are SATAII 3G drives, and they will be used to collect a large amount of data, so I want to try to maintain as much performance as possible.  

One thing I did try, in a feeble attempt to get the Promise TX2300 to work, was install a Ubuntu 6.10 Server as a Virtual Machine to my workstation, and then compile the driver.  Once I had the driver, and had the Ubuntu install ask for the driver disk, I inserted the disk and Ubuntu said it couldn't read the disk. *shrug*

---

### Post by BitHosts on 2007-04-12
Erm, someone correct me if im wrong but I thought all "true-raid" solutions hid the disks from the operating system by acting as its own BIOS thus meaning when installing that Ubuntu or whatever for that matter just sees a *hopefully* giant hard disk?

For what its worth I just set up a similar sounding box with an Adaptec 2420SA with 4 500Gb Hard Disks and that worked a treat with Ubuntu thinking that it had a 1.4Tb hard disk.

---

### Post by dcastellani on 2007-04-12
True raid is usually the hardware doing all the work for the striping/mirroring/etc.  Fakeraid is usually reffered to the cards that use the system resources and software/driver to process the same tasks that a true hardware raid controller does on its own.

The Adaptec you described is a true hardware raid controller.  I might see about getting that, looks like a great card.  Thanks for the tip!

---

