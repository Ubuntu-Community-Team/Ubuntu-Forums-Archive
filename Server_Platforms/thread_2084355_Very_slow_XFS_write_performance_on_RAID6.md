---
title: "Very slow XFS write performance on RAID6"
date: 2012-11-15
forum: Server Platforms
---

### Post by sierraEcho on 2012-11-15
I've been trying to locate the problem that is causing extremely slow write performance on a RAID 6 array with an XFS filesystem on it, but despite days at it I can't locate the problem, can anyone help?

System is Ubuntu 12.10 32 bit.

RAID is a 7 disk RAID 6 Linux software raid using 3TB SATA disks, each disk has a single gpt partition occupying the whole disk, and the raid is using a 256k chunk size.

Reading from the filesystem works at the sort of speed I expect, I get up to 360MB/s, but writes run at just 11MB/s (dd if=/dev/zero of=deleteMe bs=1M count=1000). 

I've tried boosting stripe cache size, now at 16MB, but it never uses more that 4MB. 

Read-ahead cache for each disk is set at 8MB, and 64MB for the raid device.

Filesystem is mounted with the options noatime,sunit=512,swidth=1536

xfs_info reports:

```
meta-data=/dev/md127             isize=256    agcount=32, agsize=114458368 blks
         =                       sectsz=512   attr=2
data     =                       bsize=4096   blocks=3662667200, imaxpct=5
         =                       sunit=64     swidth=320 blks
naming   =version 2              bsize=4096   ascii-ci=0
log      =internal               bsize=4096   blocks=521728, version=2
         =                       sectsz=512   sunit=64 blks, lazy-count=1
realtime =none                   extsz=4096   blocks=0, rtextents=0
```
CPU utilisation is low during testing, with the raid6 process consuming about 3% according to top.  CPU is an AMD FX-4100 Quad.


Any guidance appreciated, everything I can find online is just pointing me to things I've already checked.


Thanks

---

