---
title: "Lost USB mounting"
date: 2016-02-09
forum: Server Platforms
---

### Post by Riback on 2016-02-09
Why would my Ubuntu server suddenly stop mounting USB flash drives?
It has been running for 2 years no problem but since last week when I plug in a USB flash drive it tells me failed to mount.

I have made no changes to the system so for a change was not something I did.
I tried to mount manually but that also did not work

What else should I be looking at?

---

### Post by howefield on 2016-02-09
Thread moved to the "*Server Platforms*" forum.

---

### Post by nerdtron on 2016-02-09
All USB devices fails to mount? or just a single usb flash drive

---

### Post by Riback on 2016-02-11
this is a strange one - Ubuntu on my HP Microserver but running desktop version 12.04 LTS 
If I insert one USB drive it fails to mount - tried then inserting another USB drive and the second one mounted. Then if I removed the first one and re inserted it also mounted. Have tried various USB drives and similar happens all the time except sometimes it takes up to the 3rd drive to be inserted before it mounts.

---

### Post by MAFoElffen on 2016-02-12
Sometimes it has to do with the USB drive or the USB connection between.

On my thumb drives and the usb ports of my servers I use 4" usb extension dongles so that if I have ports that I continually plug in thumb drives, that they take the wear. On thumb drives that I use, I plug into the dongles, so that they don't get broken (usually a soldering problem on the card. I learned this from experience of College computer labs, were ports are plugged into thousand of times a year. I now buy them in bulk for $1.50 off Ebay. You would be surprised how many ports we had go out, before we learned to sacrifice cables instead. That and having to recover thumb drives, where the students I would tudor would accidentally hit the drives with their knees and break them. 

On some drives, use fschk to look for open files in the filesystem. Very common with thumb drives to have someone pull one in the middle of a write, without first umounting the drive.

Next is the use of:
```

sudo lsusb

```
to list connected usb devices.

---

