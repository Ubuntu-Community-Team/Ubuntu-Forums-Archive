---
title: "Vmware virtual machine physical drive problem"
date: 2007-11-24
forum: Virtualisation
---

### Post by Partyboi2 on 2007-11-24
I have installed vmware server, but I have run into a problem setting up the virtual machine. I am trying to set it up so that I am using a Physical windows drive, as I have xp on my other drive.
I have been following instructions here:
[http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/](http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/)
But I run into problems when I get to this part:

> **Use individual partitions** and pick both your Window NTFS and Linux Ext3 partition (since part of Grub is on your Linux partition). Don’t bother about the swap partition.When I get to individual partitions I can only choose one, sdb or sda. 
I have 2 physical hard drives, one (sda) has my windows system and my ubuntu /home.
On the second drive (sdb) is where ubuntu is installed.
How can I get around this problem? Cause I think this guide is more for if you have one hard drive.
Is it possible to get vmware setup with the way my partitions/drives  are setup?

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfeebaf6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10261    82421451    c  W95 FAT32 (LBA)
/dev/sda2           13055       19457    51432097+  83  Linux
/dev/sda3           10262       13054    22434772+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a2e2a2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               1        4865    39078081    5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris
/dev/sdb6               1        4660    37431355+  83  Linux

Partition table entries are not in disk order
```
Thanks for any help

---

### Post by Partyboi2 on 2007-11-27
I guess nobody has run into this kinda problem before.

---

