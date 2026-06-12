---
title: "RAID1, how is it supposed to work?"
date: 2009-07-07
forum: Server Platforms
---

### Post by Jeinhor on 2009-07-07
I had a RAID1 setup on two harddrives. Recently, one broke which I didn't notice directly. However, at the next boot up, it wanted to do a fsck. After it did (got some errors), I couldn't boot it at all anymore. "Grub error 17".

Seems pointless to have a RAID1 if it breaks the whole array when one disk goes down. How is it supposed to be? Should I have aborted that fsck (I was asked to run it manually)?

Thanks in advance!

---

### Post by TwiceOver on 2009-07-07
To me it sounds like grub was damaged during the failure of the one disk (maybe grub was magically only on one of the disks MBR?).

The other disk was probably good, but needed a new grub install to get it to boot again.

Just my thoughts.

---

### Post by Jeinhor on 2009-07-07
Thank your for the reply!

I tried repairing using Super Grub Disc, but I might have tried to repair the wrong disk. I also tried mounting the root file system using Ubuntu Restore mode, but it didn't work (this time I was using only the working disc, but it said it couldn't mount the md0 device).

When I installed the RAID I did set the "bootable" flag on both partitions participating in the RAID1 array. Wouldn't this install grub on both?

---

### Post by drave99 on 2009-07-08
grub is not autmatically installed into the boot sector on both disks, it has to be done manually

see: [http://www.texsoft.it/index.php?c=hardware&m=hw.storage.grubraid1&l=it](http://www.texsoft.it/index.php?c=hardware&m=hw.storage.grubraid1&l=it)

---

### Post by Jeinhor on 2009-07-08
I'd say it does in the new 9.04 version, see: [http://ubuntuforums.org/showthread.php?p=7577193](http://ubuntuforums.org/showthread.php?p=7577193)

=)

---

