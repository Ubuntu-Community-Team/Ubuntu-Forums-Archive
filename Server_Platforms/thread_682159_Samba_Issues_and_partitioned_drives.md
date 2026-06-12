---
title: "Samba Issues and partitioned drives"
date: 2008-01-29
forum: Server Platforms
---

### Post by matthewboh on 2008-01-29
Okay - I've been having troubles with Samba and I THINK I've tracked it down - before I go any further, just wanted to get some feedback.

Anyway, have a LAMP server with Ubuntu and two hard disk drives.  I'm using the second one for the Samba file shares.  However, during install, it only ran fdisk on the first drive, and if I run 

```
sudo fdisk -l /dev/sdb1

Disk /dev/sdb1: 40.0 GB, 40015471104 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb1 doesn't contain a valid partition table

```

So I figure I have to partition.  However, there's talk about NTFS vs. ext3 vs. ntf2-3g.  If I want to use this drive as a Samba share with both Ubuntu and Windows machines - what should I use?

Also, what do I need to know to properly re=partition my drive?

Thanks

---

### Post by luisromangz on 2008-01-29
If you only plan to use it for sharing, so you aren't going to create a dual boot system, your most reasonable option is using the ext3 partition format.

---

