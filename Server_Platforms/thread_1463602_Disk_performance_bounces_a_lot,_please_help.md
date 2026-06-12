---
title: "Disk performance bounces a lot, please help"
date: 2010-04-27
forum: Server Platforms
---

### Post by tarekeldeeb on 2010-04-27
Hello all,

I have a NFS server with a raid device for data. I recognize that the throughput differs a lot through time. On a GiEthernet it ranges from [1-90] MBps with an average ranging from [15-60] MBps.

I wanted to test the disk speed, as I think the NFS server is not loaded that much.

I found weird behavior, please see my tries below.

```

[root@server md0]# time dd if=/dev/zero of=test.tst  bs=4k count=81920
81920+0 records in
81920+0 records out
335544320 bytes (336 MB) copied, **2.577** seconds, **130 MB/s**

real    0m**10.580s**
user    0m0.010s
sys     0m0.641s

[root@server md0]# time dd if=/dev/zero of=test.tst  bs=4k count=81920
81920+0 records in
81920+0 records out
335544320 bytes (336 MB) copied, **0.493557 **seconds, **680 MB/s**

real    0m**10.874s**
user    0m0.003s
sys     0m0.616s
```

I have 2 questions, I hope someone can clarify them:

Q1- What causes this slow/toggling performance between 130 and 680 MBps ? Can I configure bigger buffers for such an issue?

Q2- I see the real time far beyond that reported by 'dd', will applications (NFS server) see this real time and suffer much less performance?

Thanks in advance,
Tarek

---

### Post by uberlinuxnerd on 2010-04-27
To get a more realistic result don't use /dev/zero, instead use /dev/urandom and post back your results.

---

### Post by dragos2 on 2010-04-27
It depends on what type of RAID do you have. If its a RAID5 when you write data it needs to do parity calculations and depending on the controller implementations they can bottleneck sometimes the write throughput.

Try to use vmstat 1 while you are doing the dd test, also don't use /dev/zero.

Use a bigger file like 10 GB, and test for different sector sizes like 4, 16, 32, 64, etc up to 1024.

---

### Post by tarekeldeeb on 2010-04-27
Thank you uberlinuxnerd and dragos2 for your help,

Yes I use RAID5, with the following details:
```
# mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Sun Jan 10 20:13:56 2010
     Raid Level : raid5
     Array Size : 976558592 (931.32 GiB 1000.00 GB)
  Used Dev Size : 488279296 (465.66 GiB 500.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Apr 27 16:28:45 2010
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 256K

           UUID : 6bd54d2d:7a03bb5e:452caa78:03014ee9
         Events : 0.137

    Number   Major   Minor   RaidDevice State
       0       8       34        0      active sync   /dev/sdc2
       1       8       18        1      active sync   /dev/sdb2
       2       8        2        2      active sync   /dev/sda2
```

> Use a bigger file like 10 GB, and test for different sector sizes like 4, 16, 32, 64, etc up to 1024.
Oohh !!!
Using /dev/urandom, I got a constant value of 8.3MB/s for all sizes.
I believe this is too low!


This snapshot is during a dd run:
```
# vmstat 1
procs -----------memory---------- ---swap-- -----io---- --system-- -----cpu------
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 1  0    160  23588  71448 3458644    0    0   202   102   10    5  1  1 95  3  0
 1  0    160  24240  71456 3457980    0    0     0     0 1048  199  0 50 50  0  0
 1  0    160  24632  71464 3457288    0    0     0   124 1111  264  0 50 50  0  0
 1  0    160  25148  71444 3456864    0    0     0 31772 1259  457  0 53 47  0  0
 1  0    160  26036  71460 3456140    0    0     0  8732 1124  309  0 51 44  6  0
 1  0    160  26552  71476 3455680    0    0     0    32 1066  253  0 50 50  0  0
 1  0    160  23616  71484 3459376    0    0     0     0 1058  224  0 50 50  0  0
 1  0    160  24256  71484 3458636    0    0     0 22620 1220  443  0 52 49  0  0
 1  0    160  27180  71508 3455988    0    0     0 17972 1182  399  0 52 43  6  0
 1  0    160  23872  71516 3459692    0    0     0     0 2748 2690  0 53 47  0  0
 1  0    160  24388  71524 3459096    0    0     0     0 1107  319  0 50 50  0  0
 1  0    160  24780  71528 3458348    0    0     0     0 1163  349  0 50 50  0  0
 1  0    160  25172  71520 3457856    0    0     0 19296 1357  658  0 52 48  0  0
 1  0    160  26060  71508 3457424    0    0     0 21836 1334  545  0 52 42  7  0
 2  0    160  26700  71496 3456752    0    0     0     0 1155  341  0 51 49  0  0
 1  0    160  27092  71412 3456384    0    0     0     0 1081  273  0 50 50  0  0

```

Now I have two questions:
1- Is /dev/urandom the bottleneck? 
 I also tried  dd if=/dev/sda1, this gave 500+MB/s
2- How can I test the overheads of the parity calculations?

I still did not -for sure- know my disk IO speed!

Thanks for your time.
Tarek

---

