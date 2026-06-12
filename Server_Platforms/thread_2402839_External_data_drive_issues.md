---
title: "External data drive issues"
date: 2018-10-04
forum: Server Platforms
---

### Post by simonlap on 2018-10-04
Hello,

I am running ubuntu 18.04 server version. 

I have issues with an external USB drive that I use as data folder on the server. It's a USB3.0 drive.

The first issue I have is everytime the system reboot, it won't see the external drive SDB - SDB1. Everytime I need to unplug it and plug it back in so I can see it using command line : lsblk

Second issue is that this drive is mount to /media/Data in order to share it using Samba on my network. Now everytime I need to mount it using command line : mount /dev/sdb1 /media/Data

I would like to know if there are ways to fix this. Note that I am new to this, it is my first Ubuntu server.

Thanks!

---

### Post by TheFu on 2018-10-05
The power to mount is the power to destroy.  Remember that.
There are different solutions based on the type of data, how the data is accessed, and whether the drive is 100%, always connected or just connected 99.99999%  of the time.

First, the external drive is portable, correct?  Do you ever move it somewhere else?  Is it ever not powered on?  Backup disks shouldn't always be connected to the system they backup, for example.

Is the device ever connected directly to a Windows computer?
Which file system is on the disk?

---

### Post by simonlap on 2018-10-05
So the drive I use is an external drive always powered with a PSU and it's directly plugged in the ubuntu server with a usb. The PSU is plugged in a backup PSU so I would say that the drive is powered and connected to the server at all times. It never moves. 

It's connected directly to the Ubuntu server. 

Here's the output of df -T :
Filesystem     Type      1K-blocks      Used  Available Use% Mounted on
/dev/sdb1      fuseblk  1953512032 291034560 1662477472  15% /media/Data

When the server reboot, I can't find the sdb1 drive unless I manually unplug it and plug it back in. Yet - I can see it using lsusb but not using lsblk.... 

Thanks for the help!

---

### Post by TheFu on 2018-10-05
Which file system?

If you are 100% positive about things, then I'd push for the file system to be ext4, the partitioning to be GPT, and then you can mount it somewhere outside /media (to avoid future conflicts) using the /etc/fstab.  As it is mounted today, using FUSE, the access will always be slower.  It probably has NTFS, which will always be less integrated than running a native Linux file system that supports full Unix permissions, ACLs, extended attributes and user extended attributes. I've never tried to share an NTFS partition over samba, seems counter intuitive to me.

---

### Post by simonlap on 2018-10-15
Yes - you are correct this FUSE means it has NTFS. 

> [COLOR=#000000]If you are 100% positive about things, then I'd push for the file system to be ext4, the partitioning to be GPT, and then you can mount it somewhere outside /media (to avoid future conflicts) using the /etc/fstab.[/COLOR]

I am really new to linux stuff and all, so this means I need to format the drive in order to change the filesystem and partion? Any tips on how I should process, I have no clue what to do. I started to have a "logical block async page read" error today with that same drive...

Sorry, it took a week to answer, I was out of town for the last 6 days. 

Thanks for all the help!

---

### Post by TheFu on 2018-10-16
If you see any errors on a disk, get religious about your backups.  Do them as often as you cannot stand to loose data.  Every 24 hrs is common, that way, you don't lose more than the last 24 hrs of changed/updated data.

Everything else is secondary to figuring out and fixing the disk issues.  I would use SMART data to decide if this was a problem with the disk, a cable or something else.  There are probably GUI tools for that, but I use **smartctl**.  The real power with SMART disk data is watching how it changes over time. Looking at it once isn't enough.

Solve that problem first.

As for the other stuff, Linux has 20+ different file systems, each is optimized for different uses and a few  are good for general purpose use.  If you don't have a specific reason to use one of the specialized file systems, then using ext4 is a good, general, choice.  Ext4 is fast enough, holds large files, can be resized larger easily.  Can be shrunk with a little effort, and works well with nfs, samba/CIFS, and supports **all** the Unix, Posix, permissions expected.  For a single drive setup, **gparted** can be used to make a GPT partition table, create 1 or more partitions, and format each to ext4. There are many other programs that can do each part, so you might want to use those instead. I don't know. Just depends.

---

