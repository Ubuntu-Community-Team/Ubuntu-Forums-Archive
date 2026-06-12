---
title: "Incredibly slow usb in xp guest"
date: 2009-12-30
forum: Virtualisation
---

### Post by bcoffield on 2009-12-30
Hi,

Thread title pretty much says it all but...

Running 9.10 with the latest personal edition of virtualbox and have XP Pro up and running smoothly.  The only thing is that the usb transfer rates are just abysmally slow.  I have searched around for this and there seem to be tickets open in virtualbox for this... and in this forum and others I have seen people complaining of the same issue but I have found no solutions.

Writing this in the hopes that someone does have a solution.  (Or at least to collect a long list of people having the same issue:)  Thanks!

---

### Post by joshedmonds on 2009-12-31
If you require access to the drive as a storage device, but not necessarily as a USB device, you could specify a mount point in FSTAB (not necessarily necessary if it has a label, but just to make sure it always mounts in the same place) and share that folder with the XP guest.

---

### Post by bcoffield on 2010-01-01
Josh,

That's a great idea and I will do that for my external hard drive.  Unfortunately also of issue are things like syncing my ipod and digital camera etc through usb...

---

