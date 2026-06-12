---
title: "Puzzling - mdadm RAID6 slow only over iSCSI"
date: 2010-12-13
forum: Server Platforms
---

### Post by pneumatic on 2010-12-13
I have an 8 disk mdadm RAID6 and performance is charted below.  I have no issues copying a 3 gigabyte file back and forth but, when I try over iSCSI (via SCST), the transfer speed is fine (~100MB/s) for a few hundred megs and than slows to about 20MB/s.  I've tried different chunk sizes and what not but can't seem to figure this out.

Basic SATA disks work fine across the same iSCSI connection (~100MB/s) so I know that it isn't the network aspect.  Everything works fine when I enable SCST caching but I need to disable it for DRBD replication (VMware active-active).

Anyone?

EDIT - I'm starting to think that the iSCSI 512 byte blocks are correlating just fine with this write performance.  Is software RAID6 just this bad or am I doing something wrong?  This is a dual quad Xeon 5504 box with 24GB of RAM.

```
blocksize        W        W        W   W(avg,   W(std,        W        R        R        R   R(avg,   R(std,        R
  (bytes)      (s)      (s)      (s)    MB/s)    MB/s)   (IOPS)      (s)      (s)      (s)    MB/s)    MB/s)   (IOPS)
 67108864    3.799    3.703    3.710  274.022    3.190    4.282    1.532    1.504    1.580  665.712   13.462   10.402
 33554432    3.935    3.834    3.874  263.880    2.797    8.246    1.573    1.494    1.559  664.477   15.001   20.765
 16777216    3.942    3.975    4.252  252.736    8.451   15.796    1.732    1.483    1.686  629.584   43.413   39.349
  8388608    6.246    5.876    5.169  178.771   14.303   22.346    2.017    1.534    1.475  623.066   82.272   77.883
  4194304    7.557    7.170    7.132  140.634    3.640   35.159    1.655    1.422    1.412  687.958   49.010  171.990
  2097152   12.012   12.486   13.270   81.477    3.322   40.739    1.775    1.486    1.401  665.565   64.971  332.782
  1048576   22.508   20.525   21.341   47.790    1.799   47.790    2.334    1.605    1.479  589.830  109.108  589.830
   524288   44.100   44.905   43.349   23.215    0.334   46.430    3.038    2.048    2.020  447.967   78.466  895.934
   262144   85.286   85.241   85.368   12.005    0.007   48.020    3.354    2.489    2.567  371.892   47.340 1487.568
   131072   97.934   96.758   95.421   10.590    0.113   84.721    4.963    4.637    4.352  220.811   11.835 1766.486
    65536  124.370  115.205  116.221    8.644    0.292  138.308    8.315    8.010    8.074  125.936    2.016 2014.984
    32768  159.964  158.576  158.255    6.443    0.030  206.181   10.236    9.675    9.786  103.505    2.497 3312.149
    16384  272.476  271.494  270.656    3.771    0.010  241.349   13.943   13.929   13.738   73.834    0.501 4725.359
     8192  493.836  493.756  489.816    2.079    0.008  266.156   27.807   27.300   26.937   37.450    0.487 4793.577
     4096  965.764  981.482  964.968    1.055    0.008  270.063   33.595   33.380   33.416   30.600    0.086 7833.713

```

---

### Post by EnabrenTane on 2011-12-04
I have similar issues. I had everything working fine at one point but have never gotten back to full throughput. I have a 8x1TB raid 6 of sata drives exported as an iSCSI target (connecting from Win 7) I have tried Hardware raid 5, and software raid 6 and get about 20-40MB/s after the send cache backs up. I have tried changing MTU from default and jumbo, point to point links and multipath all to no avail. I once thought it was a bottleneck of LVM when I was running over it, but I see this issue without LVM as well.

As I recall the only time I actually saturated gigabit was when I had 4x1TB hardware raid 5 and the iSCSI server was running 9.04 i think. Since then I have never achieved max throughput despite many hours of playing with config files, packages, and configurations. iostat -xm 10 10 usually indicates high IOWait% with the parity drives more busy than the rest. The raid box is a AMD 955 x4 @ 3.2 Ghz / 8GB DDR3 1333

If anyone has a suggestion that I might over looked I am sure the OP and I would love to hear this.

---

### Post by bluesteel on 2012-12-31
I had the same issue; 8 disk MDADM RAID6 array giving ~40MB/sec writes when accessed via iSCSI, while simple testing with `dd` would yield 100-150MB/sec writes to the array locally.

I solved it by switching my iSCSI target to use "write-back" caching; rather than "write-through", which is the default. With this I now get 100-150MB/sec writes (which is basically the limit of the sil3132 and port multipliers I'm using.)

To do this I simple edited the iSCSI Enterprise Target's configuration file, and added an extra entry on the line defining my iSCSI target.

> sudo nano /etc/iet/ietd.conf

find the line that lists your iSCSI target, and change the IOMode to writeback:

> Lun 0 Path=/dev/md0,Type=fileio,**IOMode=wb**

Basically, with write-through operation every single IO operation has to be synchronised immediately, which requires multiple read operations for every sector that needs to be written to disk. Since RAID5/RAID6 calculate a parity and store this on one or more disks, each single block write operation requires the data from the adjacent blocks on the other member disks.

With writeback caching, the array is allowed to accumulate a (small) backlog of sectors to be written, which is great for sequential data written to a RAID5/RAID6 volume (as we don't have to read the sectors off all other member disks to calculate parity, when we simply write new data to all member disks at the same time)

I hope this can help others who stumble on this thread. :)

---

