---
title: "How hard is it to create an OS on CD/DVD?"
date: 2005-09-23
forum: Server Platforms
---

### Post by Nate Finch on 2005-09-23
Here's my idea, please let me know how feasible it is - 

Install ubuntu on a hard drive, set everything up the way I like, and then take a snapshot of the OS and burn it to a CD/DVD.  Shut down the computer, disconnect the hard drive, then boot from that CD/DVD, and the OS is effectively incorruptible.   if I ever want to change something, reconnect the hard drive, modify it, test it, etc.  When I'm happy with the changes re-snapshot, re-burn.

My plan is to use this as a web server.  I'd have any data that needed to be modifiable (databases, etc) on a hard drive drive, but have as much of the OS on an optical disk as possible.  

So here's the question - is this doable?  Is there an easy way to take a snapshot of the OS and put it on a disk so that it's runnable and bootable from that disk?  Preferably something that can be initiated pretty quickly (don't want to have to spend an hour every time I take a snapshot).

I know you can make an OS on a CD (like the Live CD)... so how hard is it to make one of those?

-Nate

---

### Post by mlomker on 2005-09-23
> 
I know you can make an OS on a CD (like the Live CD)... so how hard is it to make one of those?


Not particularly easy because everything has to run from a RAM disk.  I suspect that a more feasible thing would be to install everything to a hard disk but configure the fstab to mount / as read-only.  In order to do that you'd have to have a separate /dev partition (and probably other things that I don't know about)--you have to be able to write to devices.

---

### Post by az on 2005-09-23
[http://packages.ubuntu.com/hoary/utils/bootcd](http://packages.ubuntu.com/hoary/utils/bootcd)

This is what this package is for.  I used this a few years ago.  It worked great, then.  

Let me know.



The long description:
Package: bootcd (2.45) [universe]
run your system from cd without need for disks

This Package should be installed on a system with CD- or DVD-Writer. Copy your running Debian System on CD with the command bootcdwrite. If your system has no CD-Writer you can build a bootcd via NFS on a remote System with CD-Writer or you can only create an ISO image. When you run your system from CD you do not need any disks. All changes will be done in ram. To reuse this changes at next boot time you can save them on FLOPPY with the command bootcdflopcp. If booting from your CD-drive is not supported, booting from FLOPPY is possible. It is possible to install a new system from the running CD with the command bootcd2disk. Bootcd2disk can also find a target disk, format it and make it bootable automatically. Bootcd also supports initrd root fs, devfs, transparent-compression ISO 9660 fs and syslinux/isolinux.

---

### Post by mlomker on 2005-09-23
> 
This is what this package is for.  I used this a few years ago.  It worked great, then.  


That is **so** cool.  I'm going to look at that.  I've been thinking about building a custom sysresCD since I can't get the standard 2.4 kernel to boot on my box.

---

