---
title: "How to remove Luks encryption for device usb, or HD ?"
date: 2023-06-25
forum: Security
---

### Post by HuTkW$* on 2023-06-25
Hello,

I have some sd-card, usb stick and hard disk with luks encryption with password.
Looking for removing such a security layer in order to use them as a classic storage device.

Searching internet does not provide serious, official solution, tutorial for that.

Any idea of a solution please ?

Thanks !

---

### Post by ixeous on 2023-06-25
A simple reformat should take care of it.  Perhaps use fdisk, gparted or similar to delete the partions and create new one.  All data will be lost when doing that.

---

### Post by HuTkW$* on 2023-06-26
No, reformating leave the device unusable ...

---

### Post by Rubi1200 on 2023-06-27
It is possible, I believe, to do what you want.

However, the Arch wiki page has tons of warnings!
[https://wiki.archlinux.org/title/Removing_system_encryption](https://wiki.archlinux.org/title/Removing_system_encryption)

Note, I have not tried this nor do I know what possible side-effects there might be.

---

### Post by HuTkW$* on 2023-06-27
Thanks !

---

### Post by TheFu on 2023-06-27
> **exystenz said:**
> No, reformating leave the device unusable ...

That's a different issue, probably.

I've removed the partition table via gdisk/sgdisk clear option, created a new partition table and formatted the partitions. It works.  I did this on an m.2 SATA SSD in an external USB3 enclosure.  Of course, doing this wipes all data on the storage, so get everything you like off it.

Worst case, you can zero the first 4KB using dd or ddrescue, but that shouldn't really matter if you use gdisk 

```
$ sudo sgdisk --clear /dev/sdZ
```
will remove any partition table.  Chance sdZ to point at your specific _whole drive device_, not just a partition.  Be careful. If you get the wrong device, it will be a very, very, bad day.

---

