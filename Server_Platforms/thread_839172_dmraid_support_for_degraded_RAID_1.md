---
title: "dmraid support for degraded RAID 1"
date: 2008-06-24
forum: Server Platforms
---

### Post by msghaleb on 2008-06-24
Hi Everyone,

I have a quick question does dmraid support degraded RAID 1?

Ok the Story is:

I've an Intel chipset (Intel® Matrix Storage Manager) so I followed the following link to install Ubuntu on this FakeRAID

[http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/]("http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/")

Now I tried to shutdown, remove one of the disks and boot back up, however I got the following Errors (after Grub)

[B]unsupported map state 0x2 on /dev/sda for SYSTEM
ERROR: adding /dev/sda to RAID set "isw_xxxxxxxxxx"
ERROR: removing RAID set "isw_xxxxxxxxxx"
No RAID sets[/B]


Also the Bios says RAID is degraded

**Does anyone knows how can I configure dmraid to support degraded RAID 1?**

I found the below tip but no idea how to check that:
[http://osdir.com/ml/linux.ataraid/2004-11/msg00018.html]("http://osdir.com/ml/linux.ataraid/2004-11/msg00018.html")

[I]see the metadata definitions for raid_dev and raid_set, how those get
silled in in isw.c and used by activate.c.
Support for degraded RAID1 set resynchronization can be worked in,[/I]

Any Help will be much appreciated

---

