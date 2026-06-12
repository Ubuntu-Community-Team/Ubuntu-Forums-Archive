---
title: "15K/sec rebuild speed on mdadm RAID6 array"
date: 2011-07-18
forum: Server Platforms
---

### Post by tehk on 2011-07-18
```

$cat /proc/mdstat                                                                                                                                                                                                                 

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdd[2] sde[3] sdc[4] sdb[0]
      1953524992 blocks level 6, 64k chunk, algorithm 2 [4/3] [U_UU]
      [>....................]  recovery =  0.1% (1176400/976762496) finish=1075045.3min speed=15K/sec

unused devices: <none>

```


1/4 of my drives died after about 3 years of usage. I replaced it with an identical drive and did a mdadm -add to re-add it to the array. I expected this to take quite a long time, but not more than 1 million minutes to complete! Can anyone offer what's going on here?

---

### Post by tehk on 2011-07-18
more info >>

```
$ sudo mdadm -D /dev/md0 
/dev/md0:
        Version : 00.90
  Creation Time : Wed Nov 26 23:17:40 2008
     Raid Level : raid6
     Array Size : 1953524992 (1863.03 GiB 2000.41 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jul 18 20:49:08 2011                                                                                                                                                                 
          State : clean, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : bbbbbbbb:cccccccc:dddddddd:eeeeeeee
         Events : 0.4002030

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       4       8       32        1      spare rebuilding   /dev/sdc
       2       8       48        2      active sync   /dev/sdd
       3       8       64        3      active sync   /dev/sde

```

---

### Post by tehk on 2011-07-18
Think I found the bottleneck...

```

$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:     2 MB in 19.77 seconds = **103.60 kB/sec**
 Timing buffered disk reads:    2 MB in  7.35 seconds = **278.55 kB/sec**

$ sudo hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   3402 MB in  2.00 seconds = 1701.11 MB/sec
 Timing buffered disk reads:  350 MB in  3.01 seconds = 116.20 MB/sec


$ sudo hdparm -tT /dev/sdd

/dev/sdd:
 Timing cached reads:   3462 MB in  2.00 seconds = 1730.52 MB/sec
 Timing buffered disk reads:  254 MB in  3.21 seconds =  79.21 MB/sec

$ sudo hdparm -tT /dev/sde

/dev/sde:
 Timing cached reads:   3274 MB in  2.00 seconds = 1636.69 MB/sec
 Timing buffered disk reads:  310 MB in  3.01 seconds = 102.91 MB/sec


```

---

### Post by tehk on 2011-07-18
```
$ sudo hdparm -i /dev/sdb

/dev/sdb:

 Model=ST31000340AS, FwRev=SD15, SerialNo=5QJ0X7TA
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode
```

---

### Post by tehk on 2011-07-18
```
$ sudo mdadm --manage --set-faulty /dev/md0 /dev/sdb
mdadm: set /dev/sdb faulty in /dev/md0

```

Set the drive to faulty so that sdc could at least rebuild fast...

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdd[2] sde[3] sdb[4](F) sdc[5]
      1953524992 blocks level 6, 64k chunk, algorithm 2 [4/2] [__UU]
      [>....................]  recovery =  0.7% (7479652/976762496) finish=609.3min speed=26511K/sec

unused devices: <none>

```

But I don't know what to do to diagnose the problem with sdb being so slow... any ideas?

---

### Post by tehk on 2011-07-18
Swapped the cable on sdb, and it was back to full speed :KS

---

