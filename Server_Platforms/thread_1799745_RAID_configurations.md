---
title: "RAID configurations"
date: 2011-07-08
forum: Server Platforms
---

### Post by Buntubailey on 2011-07-08
Please forgive me if this has been covered but I can't find anything through search. Anyway, I have been given a server that I wish to use as a file server, with remote access through VPN. The server has 4 500GB disks. I would like to have 2 of the disks combined to appear to be 1TB and the other 2 x disks to be combined for the mirror. I understand this is a basic question but I am new to this and would appreciate some knowledge. Which type of RAID array would help me to achieve my goal?

Thanks in advance,

Buntubailey

---

### Post by rubylaser on 2011-07-08
What you're asking for is RAID0 and RAID1, and I'm guessing you really want [RAID10]("http://en.wikipedia.org/wiki/Nested_RAID_levels#RAID_10_.28RAID_1.2B0.29")
.  This would give 1TB of space total (2 500GB mirrors added together for 1TB total), and be very fault tolerant with no parity calculations necessary.  Otherwise, if you're looking for the biggest amount of space with 4 disks while still having some protection, you might want to look at [RAID5]("http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_5"). With this, you'd end up with 1.5TB of raw storage space.

---

### Post by YesWeCan on 2011-07-08
Hi. You probably want RAID 10.
You can have a RAID1 of two RAID0 arrays, or you can have a RAID0 of two RAID1 arrays. The latter is what I use and I access it via VPN too.
[https://help.ubuntu.com/11.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/11.04/serverguide/C/advanced-installation.html)

Which version of Ubuntu will you use? Many guides prescribe a separate boot partition but if you use Ubuntu 11.04 it has Grub 1.99 which can boot RAID 10 directly so no separate /boot is needed.

In any case, if you use the "alternate" install ISO you can set it all up during install. You use the partitioner to create a RAID10 using your 4 disks and then you make an LVM partition on top of it. The RAID creates a single partition so you need an LVM (logical volume management) layer to be able to have multiple partitions.

That's the executive summary. It may seem pretty confusing if you are completely new to this, but once you understand the basics you should find it easy enough to set up. Have a look and come back with more questions. :)

[http://en.wikipedia.org/wiki/Non-standard_RAID_levels](http://en.wikipedia.org/wiki/Non-standard_RAID_levels)

---

### Post by Buntubailey on 2011-07-08
Thanks for all of your comments, I'm going to get to work on this this weekend so will let you know how I fare, I will be using Ubuntu 11.04 so hopefully setting up the RAID 10 will be easy, I will be sure to post back here with my results,

Thanks again.

Buntubailey

---

### Post by YesWeCan on 2011-07-08
That's interesting, I just read the Ubuntu server guide RAID link I posted...it's been a while since I read it...it sets it up in the opposite way that I did. It prescribes creating partitions on the disks first and then combining them into individual RAID arrays. What I did was to create a single RAID10 array using all 4 disks and then add an LVM layer to divide it up into partitions: / /home swap, etc.

The thing with mdadm RAID is that it can make multiple RAID "devices" (which are like partitions) out of either whole disks or individual partitions, including other RAID partitions. This is very flexible. And as I say you can add an LVM layer to allow you to subdivide a single partition into many partitions.

---

### Post by Buntubailey on 2011-07-11
Okay,

After getting the machine home, I opened it up and the 4 x 500GB drives are connected to a Adaptec 1430SA RAID card, so I have the hardware RAID card, and when I started it is configured as RAID 10 which you suggested. However, when I get to the partitioner, ubuntu tells me that a RAID device has been detected and would I like to connect to it, when I choose yes I am asked for the iSCSI IP address and port number. Because I am not connecting to the disks over a network I choose 127.0.0.1 but it keeps coming back telling me it can't find any disks, any idea where I should go from here?

---

### Post by psusi on 2011-07-11
It sounds like you chose the option to connect to an iSCSI drive.  Don't do that.

---

### Post by dancho on 2011-07-11
Perhaps my guide on how to convert a running Ubuntu installation to RAID1/RAID10 will help:

[http://iiordanov.blogspot.com/2011/04/how-to-convert-your-single-drive-linux.html](http://iiordanov.blogspot.com/2011/04/how-to-convert-your-single-drive-linux.html)

If you choose to reinstall, you can try this guide for making a fresh installation on RAID10/RAID1:

[http://iiordanov.blogspot.com/2011/07/how-to-install-linux-ubuntu-debian-etc.html](http://iiordanov.blogspot.com/2011/07/how-to-install-linux-ubuntu-debian-etc.html)

---

