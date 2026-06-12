---
title: "labeling for diskpartitions"
date: 2008-11-28
forum: The Cafe
---

### Post by quinnten83 on 2008-11-28
Hi all,
In windows, you can give your HD partition a descriptive name.
Is that also possible in linux. You know, so it isn't always refered to HDa0 or sda?
Although I know what it means, if you have many HD's it becomes difficult to remember if the partition where you had all those unique files was the sda1 or the sda0

---

### Post by ice60 on 2008-11-28
i think you can use **LABEL=** in your fstab.

NOTE: there's a reason i mainly post in the Community Cafe and that's because i can run linux fine on my boxes, but i'm useless at any kind of support lol

---

### Post by gpsmikey on 2008-11-28
Yes - gparted can label your partitions (if they are not mounted).  One way to do that is from either the "Live CD" or the "Gparted CD" (also bootable).  Seems to me there are a couple of other utilities, but that is what I have used.  You can also use the UUID of the disk (but if you think the "serial number" of a drive in windows is goofy, wait till you see what the UUID of a drive looks like.

# sudo blkid

will return a list of your partitions, their label (if present) and their UUID

mikey

---

### Post by Grant A. on 2008-11-28
> **gpsmikey said:**
> Yes - gparted can label your partitions (if they are not mounted).  One way to do that is from either the "Live CD" or the "Gparted CD" (also bootable).  Seems to me there are a couple of other utilities, but that is what I have used.  You can also use the UUID of the disk (but if you think the "serial number" of a drive in windows is goofy, wait till you see what the UUID of a drive looks like.

# sudo blkid

will return a list of your partitions, their label (if present) and their UUID

mikey

Never unmount your root or home partitions!

---

### Post by gpsmikey on 2008-11-28
Well, yes, that is true - that was why I suggested booting from either the live cd or the gparted CD - that way, the / and /home partitions have not been mounted.  But you are right- don't try it from within the OS by unmounting those partitions - you will discover powder burns on your foot most likely :)

Here are a couple of links that you may find helpful (note that the one person said that while it was for USB drives, it applied to internal drives as well)

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
[http://ubuntuforums.org/showthread.php?t=207389](http://ubuntuforums.org/showthread.php?t=207389)

mikey

---

