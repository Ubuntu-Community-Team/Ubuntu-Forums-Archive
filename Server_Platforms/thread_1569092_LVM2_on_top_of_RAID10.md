---
title: "LVM2 on top of RAID10"
date: 2010-09-06
forum: Server Platforms
---

### Post by YorYor on 2010-09-06
Hoping to get some advice from those who've been there and done that. I've read quite a few tens of pages worth of material which Google turned up, but am still not getting a lot of clarity in this.

First of all, my setup.
Dual Opteron 2354s
4 x 500GB SATA HDDs (3 x Seagate 7200.11, 1 x WD WD5000AAKS)
All disks partitioned into 4 partitions (all references to RAID mean mdadm Linux software RAID):
- 1GB for /boot (in RAID1) (md0)
- 20GB for / (in RAID5) (md1)
- balance-4GB in RAID10 (n1,f2, 128K chunks) for LVM (md10)
- 4GB for swap (in RAID5) (md9)
LVM (md10):
- 1 volume group, 903GB
- 1 logical volume with 64 Read ahead sectors, 750GB, formatted as ext3

OS: Ubuntu Hardy 8.04.4 LTS (this is providing OpenVZ services)

This is my blockdev report, after tuning - Linux originally set everything to only 256 RA.
```
RO    RA   SSZ   BSZ   StartSec     Size    Device
rw  8192   512  4096          0  976773168  /dev/sda
rw  8192   512  2048         63    1975932  /dev/sda1
rw  8192   512   512    1975995   19551105  /dev/sda2
rw  8192   512  2048   21527100  946871100  /dev/sda3
rw  8192   512  4096  968398200    8353800  /dev/sda4
rw  8192   512  4096          0  976773168  /dev/sdb
rw  8192   512  2048         63    1975932  /dev/sdb1
rw  8192   512   512    1975995   19551105  /dev/sdb2
rw  8192   512  2048   21527100  946871100  /dev/sdb3
rw  8192   512  4096  968398200    8353800  /dev/sdb4
rw  8192   512  4096          0  976773168  /dev/sdc
rw  8192   512  2048         63    1975932  /dev/sdc1
rw  8192   512   512    1975995   19551105  /dev/sdc2
rw  8192   512  2048   21527100  946871100  /dev/sdc3
rw  8192   512  4096  968398200    8353800  /dev/sdc4
rw  8192   512  4096          0  976773168  /dev/sdd
rw  8192   512  2048         63    1975932  /dev/sdd1
rw  8192   512   512    1975995   19551105  /dev/sdd2
rw  8192   512  2048   21527100  946871100  /dev/sdd3
rw  8192   512  4096  968398200    8353800  /dev/sdd4
rw   256   512  4096          0    1975680  /dev/md0
rw  4096   512  4096          0   39101952  /dev/md1
rw 65536   512  4096          0 1893741568  /dev/md10
rw  4096   512  4096          0   25060992  /dev/md9
```

My problem is with the LVM partition used to house all my data files.
Here are some reference data:
```

$ hdparm -tT (run 3 times)

Timing cached reads:   2168 MB in  2.00 seconds = 1084.19 MB/sec
Timing buffered disk reads:  806 MB in  3.00 seconds = 268.23 MB/sec

Timing cached reads:   2236 MB in  2.00 seconds = 1118.74 MB/sec
Timing buffered disk reads:  824 MB in  3.00 seconds = 274.27 MB/sec

Timing cached reads:   2172 MB in  2.00 seconds = 1086.71 MB/sec
Timing buffered disk reads:  898 MB in  3.02 seconds = 297.27 MB/sec


$ hdparm -tT --direct (run 3 times)

 Timing O_DIRECT cached reads:   484 MB in  2.03 seconds = 238.57 MB/sec
 Timing O_DIRECT disk reads:  154 MB in  3.24 seconds =  47.57 MB/sec

 Timing O_DIRECT cached reads:   750 MB in  2.00 seconds = 374.42 MB/sec
 Timing O_DIRECT disk reads:  134 MB in  3.14 seconds =  42.68 MB/sec

 Timing O_DIRECT cached reads:   628 MB in  2.00 seconds = 313.56 MB/sec
 Timing O_DIRECT disk reads:  326 MB in  3.03 seconds = 107.54 MB/sec


# writing to LVM using dd, 1000x1MB blocks = 1GB file, yes this was done while in a folder of the mounted LVM
$ sync; echo 3 > /proc/sys/vm/drop_caches; dd of=1GBfile if=/dev/zero bs=1M count=1000 (run 3 times)

1048576000 bytes (1.0 GB) copied, 3.31993 s, 316 MB/s
1048576000 bytes (1.0 GB) copied, 2.06839 s, 507 MB/s
1048576000 bytes (1.0 GB) copied, 3.16659 s, 331 MB/s


# reading 1GBfile created above (run 3 times)
$ sync; echo 3 > /proc/sys/vm/drop_caches; dd if=1GBfile of=/dev/null bs=1M

1048576000 bytes (1.0 GB) copied, 19.458 s, 53.9 MB/s
1048576000 bytes (1.0 GB) copied, 17.0205 s, 61.6 MB/s
1048576000 bytes (1.0 GB) copied, 5.1026 s, 205 MB/s


```

As seen above, the actual reading speed from the filesystem seems to be quite bad when using dd, but hdparm seems to report a fairly respectable transfer rate. The third result for dd and hdparm were conducted one after the other, so it might have been the "true" rate if the machine happened to be in a period of lull disk activity.

Granted, the above were run on an active server in production, so there might have been some impact, but surely it can't have possibly deteriorated to a level that is worse than a single disk's performance?

I then ran the same read tests on md10 itself:
```

$ hdparm -tT /dev/md10

 Timing cached reads:   2178 MB in  2.00 seconds = 1088.88 MB/sec
 Timing buffered disk reads:  602 MB in  3.00 seconds = 200.57 MB/sec

 Timing cached reads:   2086 MB in  2.00 seconds = 1043.57 MB/sec
 Timing buffered disk reads:  514 MB in  3.09 seconds = 166.21 MB/sec

 Timing cached reads:   2150 MB in  2.00 seconds = 1074.94 MB/sec
 Timing buffered disk reads:  798 MB in  3.02 seconds = 264.19 MB/sec


$ hdparm -tT --direct /dev/md10

 Timing O_DIRECT cached reads:   254 MB in  2.00 seconds = 127.00 MB/sec
 Timing O_DIRECT disk reads:  356 MB in  3.13 seconds = 113.84 MB/sec

 Timing O_DIRECT cached reads:   1316 MB in  2.00 seconds = 657.44 MB/sec
 Timing O_DIRECT disk reads:  606 MB in  3.01 seconds = 201.40 MB/sec

 Timing O_DIRECT cached reads:   1264 MB in  2.00 seconds = 631.59 MB/sec
 Timing O_DIRECT disk reads:  614 MB in  3.03 seconds = 202.86 MB/sec


$ sync; echo 3 > /proc/sys/vm/drop_caches; dd if=/dev/md10 of=/dev/null bs=1M

1048576000 bytes (1.0 GB) copied, 7.13255 s, 147 MB/s
1048576000 bytes (1.0 GB) copied, 3.949 s, 266 MB/s
1048576000 bytes (1.0 GB) copied, 4.47668 s, 234 MB/s

```

So a few questions:
1. Should I be concerned about the read speeds? The write speeds are decent and consistent it seems...

2. If yes, is there something I can do to improve the performance? It was worse when the RA was set to 256 blocks.

I did run some tests before the server went into production and the figures weren't any much better than those above. Which means that the RA tuning helped a little since it helped to improve the figures despite disk activity going into production level... but it still appears to be slower than what it is capable of?

Appreciate any advice/comments whatsoever.

---

