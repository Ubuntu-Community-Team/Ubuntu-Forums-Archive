---
title: "[SOLVED] Finalizing RAID 1"
date: 2008-11-22
forum: Server Platforms
---

### Post by victorbrca on 2008-11-22
Hi all,

 I was having some weird GRUB problem when installing my server and I ddn't pay attention when setting up my two RAID drives. 

  It's partially set, looks like waiting for the md device and a mount point. Anyone have any tips on what I should do from here?

```
$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000afe7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488386552+  fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b2bde

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488386552+  fd  Linux raid autodetect

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7a4d7a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1824    14651248+  83  Linux
/dev/sdc2            1825        2067     1951897+  82  Linux swap / Solaris
/dev/sdc3            2068       14225    97659135   83  Linux
/dev/sdc4           14226       30401   129933720   83  Linux
victor@enterprise:~$ sudo mdadm --create --verbose --auto=yes /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
mdadm: /dev/sda1 appears to be part of a raid array:
    level=raid1 devices=2 ctime=Sun Nov 16 23:44:20 2008
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid1 devices=2 ctime=Sun Nov 16 23:44:20 2008
mdadm: size set to 488386432K
Continue creating array? no
mdadm: create aborted.
```

Thanks!!

Vic.

---

### Post by fjgaude on 2008-11-22
You are booting from sdc1?

There is nothing wrong with answering "yes" to continue creating the array.

Unless you have important data on either sda1 or sdb1

I take it data on is on sdc1 and you might have copied it to sda1?

Create the raid1, put a filesystem on it, then mount and copy important data to it.

Let us know if you have any problems.

---

### Post by victorbrca on 2008-11-22
Thanks Frank. I ended up doing that yesterday night a bit after I posted it here. Got back to it this morning and the sync was done. Ran mkfs and added it to my fstab. 

I'll be storing my virtual machines in there!!


Vic.

---

