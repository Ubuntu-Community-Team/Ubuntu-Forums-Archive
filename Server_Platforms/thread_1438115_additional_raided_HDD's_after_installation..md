---
title: "additional raided HDD's after installation."
date: 2010-03-24
forum: Server Platforms
---

### Post by wanabewired on 2010-03-24
Hi,

I'm running a fresh install of Lucid server edition and I'd like to introduce a pair of software raided HDDs to run on /mnt/media along side my OS disk. I think the disks are ready to be formatted. Here's where I'm at:

OS Disc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227648+   5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

2x Additional Disks.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976760832   fd  Linux RAID autodetect

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976760832   fd  Linux RAID autodetect

Am i right in thinking I need to now format the discs through some form of software raid interface so that the ext4 filesystem I put on them is treat locally as one device and therefore one mount point?

Could do with a hand on this please.

---

