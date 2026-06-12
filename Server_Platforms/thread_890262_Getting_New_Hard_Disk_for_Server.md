---
title: "Getting New Hard Disk for Server"
date: 2008-08-14
forum: Server Platforms
---

### Post by n8dude on 2008-08-14
Please tell me if I'm not posting this in the right forum. Anyways, I have one of my older machines running ubuntu 8.04 server edition which has a 100GB HD. I have a brand new 750GB HD in the mail right now and I want to combine the 2 disks into one big partition using LVM, except I do not know how to use it. I've been googling around for a better part of an hour now, with no luck on finding a tut on how to do this. If anyone could give me a link to show me how to do this, or explain it, I will be eternally grateful. (or at least a week :P)

Edit: I would also like to do this without erasing all data on my current hard disk, is that in any way possible?

---

### Post by RealPSL on 2008-08-16
In order to use LVM it needs to write a "signature" on the disk so it is not possible to convert an existing file system to LVM. This "signature" is written when you run ```
pvcreate
```.

You can still use LVM to manage your new disk following the instructions from [howtoforge]("http://www.howtoforge.com/linux_lvm").

---

### Post by windependence on 2008-08-17
What you <could> do is get your new drive in and set it up as an LVM volume as RealIPSL suggested, then, move the data to your new drive via rsync or your favorite method, and then reload the OS using LVM for the first drive, but electing not to format the big one. You can then add the drives to your LVM group since they will have the LVM signature. It would be a little hairy, but it could be done. Even better if you just back it up to external media and then set up your LVM and restore your data.

-Tim

---

### Post by n8dude on 2008-08-17
Thanks, I may just try that. I'll give updates on how it goes.

---

