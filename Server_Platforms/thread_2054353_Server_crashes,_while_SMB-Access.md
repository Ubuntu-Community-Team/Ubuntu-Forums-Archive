---
title: "Server crashes, while SMB-Access"
date: 2012-09-07
forum: Server Platforms
---

### Post by Nephelo on 2012-09-07
Hello,

I've got a problem with my Ubuntu Server 10.04. A raid5 (mdadm) and smbd is running. Sometimes there is no problem to access the network shares. But sometimes (mostly while writing a lot of data) the server freezes and doesn't react any more. Only a reset helps. If I don't access the shares, the server runs without any problem.

The RAM seems ok (checked with Memtest) and the filesystem itself also. I created a big archive (via terminal) about 200gb and the server was running.

The system ran (about one year) without any problem.

Syslog:
> 
kernel: [    2.453227] mdadm: sending ioctl 1261 to a partition!
kernel: [    2.453230] mdadm: sending ioctl 1261 to a partition!
kernel: [    2.453461] mdadm: sending ioctl 1261 to a partition!
kernel: [    2.453464] mdadm: sending ioctl 1261 to a partition!
kernel: [    2.453819] mdadm: sending ioctl 1261 to a partition!
kernel: [    2.453823] mdadm: sending ioctl 1261 to a partition!
kernel: [    2.454047] mdadm: sending ioctl 1261 to a partition!
kernel: [    2.454050] mdadm: sending ioctl 1261 to a partition!
kernel: [    2.454123] mdadm: sending ioctl 1261 to a partition!
kernel: [    2.454124] mdadm: sending ioctl 1261 to a partition!
mdadm --detail /dev/md0
> 
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Thu Apr 28 22:56:30 2011
     Raid Level : raid5
     Array Size : 7814047744 (7452.06 GiB 8001.58 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Sep  7 10:42:38 2012
          State : active, resyncing
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 32% complete

           UUID : 634eacfa:4993b519:9ef9defe:407a6f51 (local to host homeserver)
         Events : 0.45379

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       49        1      active sync   /dev/sdd1
       2       8       33        2      active sync   /dev/sdc1
       3       8       81        3      active sync   /dev/sdf1
       4       8       65        4      active sync   /dev/sde1
The resync allways runs after the server was reset.

I hope someone can help me.

---

