---
title: "Mdadm + xfs very slow read speed after mount"
date: 2013-04-17
forum: Server Platforms
---

### Post by greyrl on 2013-04-17
After rebuilding server (full upgrade) and install new os (Ub-serv 12.04) got a nasty problem.

HDDs: 4x2Tb WD Reds (for lvl 10,5,6 tests) tested speed 140-150 MB/s, 2x1.5Tb (for lvl 1) tested speed about 110-120 MB/s
when i creating any raid (_levels 1,5,6,10 already tested - only linear mode dont has this problem_) read speed is fine 100+/200+ MB/s
making XFS with proper tags - all ok
but after i mount FS i getting terrible read speed (about 40MB/s for lvl1,10 and about 50MB/s for lvl5,6)

For example 2Tb disks
```
Disks aligned normaly for 4k (all 4 same) 


Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes (thats WD Red - with fake 512)
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00060d09


   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1           49152  3906895871  1953423360   83  Linux
```

Mdadm - different chunk (128-512) last one tested has level=5 devices=4 chunk=512 (default)

FS created: mkfs.xfs -b size=4096 -d sunit=1024,swidth=3072 -L srvz-raid5-xfs /dev/md1
*(prev tests was without -b size=4096 - same result)

FS info:
```

user@srvz:~$ xfs_info /dev/md1
meta-data=/dev/md1               isize=256    agcount=32, agsize=45780352 blks
         =                       sectsz=512   attr=2
data     =                       bsize=4096   blocks=1464968832, imaxpct=5
         =                       sunit=128    swidth=384 blks
naming   =version 2              bsize=4096   ascii-ci=0
log      =internal               bsize=4096   blocks=521728, version=2
         =                       sectsz=512   sunit=8 blks, lazy-count=1
realtime =none                   extsz=4096   blocks=0, rtextents=0

```

Tests before mount:
```

FS umounted


root@srvz:# cat /dev/md1 | pv -r > /dev/null
[ 180-194MB/s]


user@srvz:~$ dstat -D sde,sdh,sdi,sdj
You did not select any stats, using -cdngy by default.
----total-cpu-usage---- --dsk/sde-----dsk/sdh-----dsk/sdi-----dsk/sdj-- -net/total- ---paging-- ---system--
usr sys idl wai hiq siq| read  writ: read  writ: read  writ: read  writ| recv  send|  in   out | int   csw
  1   4  94   1   0   1|5509k  375B:5507k  195B:5508k  437B:5507k  252B|   0     0 |   0     1B|1365   464
  3  32  61   0   0   5|  46M    0 :  46M    0 :  46M    0 :  47M    0 |3164B 8218B|   0     0 |5000  2954
  3  32  60   0   0   6|  49M    0 :  49M    0 :  48M    0 :  48M    0 |1447B 6735B|   0     0 |6547  2873
  2  32  61   0   0   5|  46M    0 :  46M    0 :  45M    0 :  45M    0 |2540B   23k|   0     0 |4457  2849
  2  34  59   0   0   4|  48M    0 :  48M    0 :  48M    0 :  48M    0 |2951B 9693B|   0     0 |6619  3531
  2  33  60   0   0   5|  47M    0 :  47M    0 :  48M    0 :  48M    0 |2241B   42k|   0     0 |5799  2581
  2  31  61   0   0   6|  48M    0 :  48M    0 :  47M    0 :  47M    0 |2415B   31k|   0     0 |5590  2609
  2  31  60   1   0   6|  47M    0 :  48M    0 :  49M    0 :  48M    0 |2248B   31k|   0     0 |6626  2778
  3  31  61   0   0   5|  48M    0 :  47M    0 :  47M    0 :  48M    0 |3713B   56k|   0     0 |6107  2067
  2  33  60   1   0   4|  48M    0 :  48M    0 :  48M    0 :  48M    0 |2558B   24k|   0     0 |6527  2450
  2  33  60   0   0   5|  49M    0 :  49M    0 :  48M    0 :  48M    0 |3134B   35k|   0     0 |6476  2939

```


Test after mount (defaults)
```

FS mounted


root@srvz:# cat /dev/md1 | pv -r > /dev/null
[  53-59MB/s]


user@srvz:~$ dstat -D sde,sdh,sdi,sdj
You did not select any stats, using -cdngy by default.
----total-cpu-usage---- --dsk/sde-----dsk/sdh-----dsk/sdi-----dsk/sdj-- -net/total- ---paging-- ---system--
usr sys idl wai hiq siq| read  writ: read  writ: read  writ: read  writ| recv  send|  in   out | int   csw
  1   3  95   1   0   1|4124k  394B:4123k  203B:4124k  439B:4123k  242B|   0     0 |   0     1B|1095   384
  1  28  66   0   0   4|  15M    0 :  15M    0 :  15M    0 :  15M    0 |5364B   97k|   0     0 |  11k  966
  1  25  68   0   0   6|  14M    0 :  15M    0 :  15M    0 :  15M    0 |4644B  110k|   0     0 |  10k  506
  2  25  67   0   0   6|  15M    0 :  15M    0 :  15M    0 :  15M    0 |5797B  108k|   0     0 |7562   658
  1  20  71   0   0   8|  14M    0 :  14M    0 :  14M    0 :  14M    0 |6830B   91k|   0     0 |7433   592
  1  25  67   0   0   7|  15M    0 :  15M    0 :  15M    0 :  15M    0 |7503B  129k|   0     0 |  11k  646
  1  22  69   0   0   8|  14M    0 :  14M    0 :  15M    0 :  15M    0 |2951B   34k|   0     0 |  14k  627
  1  25  67   0   0   7|  15M    0 :  15M    0 :  15M    0 :  15M    0 |3927B   59k|   0     0 |  13k  604
  1  22  69   0   0   8|  15M    0 :  15M    0 :  15M    0 :  15M    0 |2784B   60k|   0     0 |  14k  589
  1  21  70   0   0   8|  15M    0 :  15M    0 :  15M    0 :  15M    0 |5456B   96k|   0     0 |  15k  796



```

Googling the problem some days and cant find solution.
Anyone have idea where's problem?

PS: system Ubuntu server 12.04 x64. tried kernel 3.2 and 3.5

---

### Post by SaturnusDJ on 2013-04-17
For performance you can use these commands to tune:
```
echo 4096 > /sys/block/md1/md/stripe_cache_size
blockdev --setra 4096 /dev/md1
```
Different sizes give different performance. For me 16k is the best with 2048k chunk for raid.

BUT, it would be strange if that's the solution.

What happens when you try these:
- 2048k chunk raid?
- ext4 fs (without any flags/parameters)?

What results do you get from this test script:
```

#!/bin/bash
dd if=/dev/zero of=/ARRAY_MOUNTPOINT/testfile bs=1M count=2000
echo 3 > /proc/sys/vm/drop_caches
sync
dd if=/ARRAY_MOUNTPOINT/testfile of=/dev/null bs=1M
```

---

### Post by greyrl on 2013-04-17
For raid5

```

user@srvz:~$ dd if=/dev/zero of=/mnt/raid5/TEST/testfile bs=1M count=2000
2000+0 records in
2000+0 records out
2097152000 bytes (2.1 GB) copied, 22.348 s, 93.8 MB/s

```
not much - 93 pretty slow
```

root@srvz# echo 3 > /proc/sys/vm/drop_caches
root@srvz:# sync
root@srvz:# dd if=/mnt/raid5/TEST/testfile of=/dev/null bs=1M
2000+0 records in
2000+0 records out
2097152000 bytes (2.1 GB) copied, 10.2054 s, 205 MB/s

```
closer

test for raid1
```

user@srvz:~$ sudo dd if=/dev/zero of=/mnt/raid1/testfile bs=1M count=20002000+0 records in
2000+0 records out
2097152000 bytes (2.1 GB) copied, 19.0119 s, 110 MB/s

```


```

root@srvz:# dd if=/mnt/raid1/testfile of=/dev/null bs=1M
2000+0 records in
2000+0 records out
2097152000 bytes (2.1 GB) copied, 20.4113 s, 103 MB/s

```



some more
```

root@srvz:# echo 3 > /proc/sys/vm/drop_caches
root@srvz:# sync
root@srvz:# dd if=/mnt/raid5/TEST/testfile of=/mnt/raid1/testfile2
4096000+0 records in
4096000+0 records out
2097152000 bytes (2.1 GB) copied, 30.5625 s, 68.6 MB/s
root@srvz:# echo 3 > /proc/sys/vm/drop_caches
root@srvz:# sync
root@srvz:# dd if=/mnt/raid1/testfile2 of=/mnt/raid5/TEST/testfile
4096000+0 records in
4096000+0 records out
2097152000 bytes (2.1 GB) copied, 33.9181 s, 61.8 MB/s




```

after your tune:

```

root@srvz:# echo 4096 > /sys/block/md1/md/stripe_cache_size
root@srvz:# blockdev --setra 4096 /dev/md1
root@srvz:# dd if=/dev/zero of=/mnt/raid5/TEST/testfile bs=1M count=2000
2000+0 records in
2000+0 records out
2097152000 bytes (2.1 GB) copied, 14.2327 s, 147 MB/s
root@srvz:# echo 3 > /proc/sys/vm/drop_caches
root@srvz:# sync
root@srvz:# dd if=/mnt/raid5/TEST/testfile of=/dev/null bs=1M
2000+0 records in
2000+0 records out
2097152000 bytes (2.1 GB) copied, 10.1351 s, 207 MB/s

```

but 
cat /dev/md1 | pv -r > /dev/null
gives same result - at total 50-60 MB/s and about 14-15MB/s per drive (with dstat -D)

---

### Post by SaturnusDJ on 2013-04-17
When only looking at the raid5 results, it quite looks like a problem I had. But my problem wasn't affected by mounting. The drives (also WD Red) got too cold and start to drop in write speed.

Have a look at [http://ubuntuforums.org/showthread.php?t=2124231](http://ubuntuforums.org/showthread.php?t=2124231). Maybe you'll find something interesting.

Like I said the tuning parameters differ for each setup (related to array chunk size also). Meaning you might get better results with something else than 4096.

Did you try an ext4 filesystem?
Did you try a larger chunk size for the array?

---

### Post by greyrl on 2013-04-17
> [COLOR=#000000]When only looking at the raid5 results, it quite looks like a problem I had. But my problem wasn't affected by mounting. The drives (also WD Red) got too cold and start to drop in write speed.[/COLOR]
dont think they cold - operating 42-44C (some hotter that i want but thats problem of 2U 8hotswap case cooling)

ext4 didnt try and really dont want - last 6 years i use xfs and like it much (for good speed and great fragmentation (last ones key)).

didnt try larger chunks: test done raid6 chunk 128,256,512 , raid5 chunk 128,512, raid10 chunk 512, raid1 ... heh its block mode :)


some more (linear mode)
```

root@srvz:# dd if=/dev/zero of=/mnt/dl/testfile bs=1M count=2000
2000+0 records in
2000+0 records out
2097152000 bytes (2.1 GB) copied, 20.3992 s, 103 MB/s
root@srvz:# echo 3 > /proc/sys/vm/drop_caches
root@srvz:# sync
root@srvz:# dd if=/mnt/dl/testfile of=/dev/null bs=1M
2000+0 records in
2000+0 records out
2097152000 bytes (2.1 GB) copied, 25.4355 s, 82.4 MB/s
root@srvz:# cat /dev/md10 | pv -r > /dev/null
[84.3MB/s]

```

only mdadm linear mode feels fine after mount (84MB/s for it is ok - its old controller on old PCI bus)

test raid5 and raid1 with ext4 ill do some later - need cros-backup data before format

but main - i cant understand how that can be:
```

root@srvz:# cat /dev/md1 | pv -r > /dev/null
**[56.8MB/s]**
root@srvz:# cat /dev/sdh | pv -r > /dev/null
[157MB/s]
root@srvz:#** umount /dev/md1**
root@srvz:# cat /dev/md1 | pv -r > /dev/null
[B][187MB/s]
[/B]root@srvz:# **mount -a**
root@srvz:# cat /dev/md1 | pv -r > /dev/null
**[56.4MB/s]**



```

---

### Post by rubylaser on 2013-04-17
> **greyrl said:**
> 
only mdadm linear mode feels fine after mount (84MB/s for it is ok - its old controller on [SIZE=4][COLOR=#ff0000]**old PCI bus**[/COLOR][/SIZE])

This is your problem.  With a PCI Bus, you are starving your disks and limiting them to 133 MB/s total across all the disks. Anything above that is due to caching and will disappear with a larger test size. To see better speeds, you really need to upgrade to PCI-express HBA.

---

### Post by greyrl on 2013-04-17
[COLOR=#000000]full system spec.
PCI-E SAS 8 port as HBA: 
connected 
4 disks 2TB (2 on 1st channel, 2 on 2nd) - used for raid 5,6,10 levels  
+ 2 disks 1.5TB (both on channel 2) used for raid 1 level
PCI SATA300 TX4 4Port: 
connected 
1 system disk 
+ 3 disks 1.5TB - using for mdamd linear mode 

as you see all test on** PCI-e **bus and it shows good speed until i mount filesystem
[/COLOR]
root@srvz:# cat /dev/md1 | pv -r > /dev/null
[B][56.8MB/s]
[/B]root@srvz:# cat /dev/sdh | pv -r > /dev/null
[157MB/s]
root@srvz:#[B] umount /dev/md1
[/B]root@srvz:# cat /dev/md1 | pv -r > /dev/null
[B][187MB/s]
[/B]root@srvz:# [B]mount -a
[/B]root@srvz:# cat /dev/md1 | pv -r > /dev/null
**[56.4MB/s]**[COLOR=#000000]
[/COLOR]

---

### Post by rubylaser on 2013-04-18
I can see that, but I can still tell you that your PCI card, even in a PCIe bus is the weak link in this scenario.  Here's something else to try to see if it is just the mounting that's slowing you down.  Blow away your mdadm array, and put an xfs filesystem on each individual disk.  Mount each disk and then try to read/write to them all at the same time and report back.  If those numbers still look good, then there is more digging to do.  For your tests, you need to use a larger test (at least 2x the amount of RAM in the box), then sync, and then run the read tests. Luckily, if you do need to upgrade your card, an IBM BR10i can be had very cheap via ebay.

---

### Post by greyrl on 2013-04-18
what you mean? > [COLOR=#000000]your PCI card, even in a PCIe bus is the weak link in this scenario.[/COLOR]
i have 2 controllers inside system. 
1st is PCIe 8 port SAS in HBA mode (has LSI 3081E and RR2680 - both tested) and only on this one i making test and keeping raids. _raids only here_
2nd is PCI 4port SATA controller - _i dont use it for raid _(no cross controller raids here) i use it for system HDD and for trash-volume HDDs.

raw assessing to all disks [COLOR=#000000]at the same time [/COLOR]gives normal speeds - no matter mounted FS or not
problem only with mdadm device and its speed test.

i'll make test you asking just need to make safe backup before

---

### Post by rubylaser on 2013-04-18
Don't worry about running the test.  I misunderstood what you wrote earlier had me believing that you were using the 4 port PCI controller for the disks in your array (shame on me for skimming :) ).  I know you want to use XFS, but have you tried this with ext4 and [tuned the array]("http://ubuntuforums.org/showthread.php?t=1494846")?  Also, what is the other hardware in this system, and what does the load look like when you run this test?

---

### Post by greyrl on 2013-04-18
all fine :) 
...

load not so much: process peaks (write raid5-6) not more that 40-48% - reads much lower. loadavg float 0.11-0.87 of 4 (some services also up)

about ext4 - yes i want to try it. after backup :) think tomorrow

---

