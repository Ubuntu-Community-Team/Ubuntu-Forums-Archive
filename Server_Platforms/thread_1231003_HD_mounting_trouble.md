---
title: "HD mounting trouble"
date: 2009-08-04
forum: Server Platforms
---

### Post by peekaboo on 2009-08-04
I moved two hard drives from one server to a newly installed server.
I'm trying to mount them.
I made a directory /media/DATA and when I type ```
sudo mount /dev/sdb /media/DATA
```
I get the following message:
> you must specify the filesystem how do I do that?

When I try ```
sudo mount /dev/sdb /media/DATA
``` I get > unknown filesystem type 'silicon_medley_raid_member'WTH?
Both drives worked fine in the old server.

Help please.

---

### Post by fahadsadah on 2009-08-04
/dev/sdb is a hard drive device, not a partition device
There should be a number after /dev/sdb, like /dev/sdb1.
If you need further assistance, please type "sudo fdisk -l" and post the output here.

---

### Post by djurny on 2009-08-04
```
cat /proc/partitions
```
doesnt need root privilges and also helps :)

normally speaking, filesystems are selected using the '-t' option to mount.. for an ext3 fs, mount -t ext3 does the job..

also have a look at
```
cat /proc/filesystems
```

if you have a harddisk containing a filesystem that needs additional kernel drivers, it should appear in /proc/filesystems.. if it does not, insmod the appropriate filesystem kernel module before mounting the disk..

hope that helps..

---

### Post by fahadsadah on 2009-08-04
-t would be correct if he had selected the correct block device.

---

### Post by djurny on 2009-08-04
> **fahadsadah said:**
> -t would be correct if he had selected the correct block device.

true, but not everyone uses a partition table on their harddrives ;)

---

### Post by peekaboo on 2009-08-04
> **fahadsadah said:**
> /dev/sdb is a hard drive device, not a partition device
There should be a number after /dev/sdb, like /dev/sdb1

That seems to have done the trick. TYVM.
I'll look into the other suggestions just so I can learn.

---

