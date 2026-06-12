---
title: "Sfill question"
date: 2009-12-11
forum: Security
---

### Post by aniplox on 2009-12-11
Hey guys I just installed sfill and I want to wipe all the free space on my hard drive

however I tried sfill /dev/sdb and it did not work. Can anyone help?

> Error: /dev/sdb is not a directory
Programming Error: sdel-lib was not initialized before calling sdel_finnish().
root@....-desktop:/home/...# sfill /dev/sdb1
Error: /dev/sdb1 is not a directory


---

### Post by lemming465 on 2009-12-12
I think *sfill* is intended for use on a mounted filesystem, not a raw disk partition.  Try something like:```
sudo -i
mkdir /media/sdb1
mount /dev/sdb1 /media/sdb1
sfill /media/sdb1
umount /media/sdb1
```
If you just want to scrub the entire drive, destroying all partitions, filesystems, and data, then a single pass of *sudo dd if=/dev/zero of=/dev/sdb bs=64k* will be much faster, and will protect you very well against nearly anyone with less resources than the NSA.

---

### Post by fireandspike on 2009-12-12
HI, I just ran [I]sudo dd if=/dev/zero of=/dev/sdb bs=64k on one of my blank drives and not only does it scrub it, it makes it completly inaccessable and screws G Parted, G Parted just sits there doing nothing when trying to look at it so I killed it and now G Parted will not even start! it tries to start then crashes!

I wanted to put a new partition on it but now I cant even get at the drive!
[/I]

---

### Post by BkkBonanza on 2009-12-12
Regarding OP question on sfill. As stated in the docs the parm given is a path on the filesystem not a device. So for example, you could do, 

sfill /home

It is a bit odd that it wants a path but the reason is that it needs to locate the filesystem you want to fill. A linux machine may have multiple filesystems mounted so it doesn't assume you want to fill / (root) for example. You tell it somewhere to start and it figures it out from there. I would have thought that a device would make more sense but I think it can't work from there because what it will do is allocate a file to fill all free space and then remove it using secure methods. So it needs to know where to create the file, not which device to use.

Regarding problem with GParted. I'm not sure why GParted can't work with the drive now, but I think it should be able to. It's just a drive wiped to zeros and not made inoperable in any way. However, you may want to try fdisk instead as sometimes I've notcied that when GParted doesn't respond correctly usually fdisk will. Or there are also other partition editors as well that are nicer than fdisk but not as fussy as GParted.

---

