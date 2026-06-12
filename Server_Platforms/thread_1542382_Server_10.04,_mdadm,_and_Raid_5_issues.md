---
title: "Server 10.04, mdadm, and Raid 5 issues"
date: 2010-07-30
forum: Server Platforms
---

### Post by jahservant on 2010-07-30
So I have a server, which I'll call "testserver".
I have a few software raids setup, and all of them were running fine until there was a power outage, and now I'm having problems with a 5-disk Raid 5 array, specifically /dev/md2, which consists of the following 1TB hard drives: sdc,sdd,sde,sdf,sdm.

The good news is, all the data is backed up so reformatting the drives and rebuilding the array from scratch is perfectly acceptable.  The bad news is that I tried this and it didn't work.

I tried destroying the array, reformatting each drive independently, and then rebuilding the array.  When I tried to rebuild the array, I get this in my inbox:
```
This is an automatically generated mail message from mdadm
running on testserver

A DegradedArray event had been detected on md device /dev/md2.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid5 sdm2[5] sdf2[3] sde2[2] sdd2[1] sdc2[0]
      3903119872 blocks level 5, 64k chunk, algorithm 2 [5/4] [UUUU_]
      [>....................]  recovery =  0.0% (100/975779968) finish=145205.3min speed=100K/sec
```

The "DegradedArray" event concerns me.  After a few hours I get this:
```
This is an automatically generated mail message from mdadm
running on testserver

A Fail event had been detected on md device /dev/md2.

It could be related to component device /dev/sdf2.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid5 sdm2[5](S) sdf2[6](F) sde2[2] sdd2[1] sdc2[0]
      3903119872 blocks level 5, 64k chunk, algorithm 2 [5/3] [UUU__]
```


Now the command "mdadm --detail /dev/md2" gives me this:
```
root@testserver:~# mdadm --detail /dev/md2
/dev/md2:
        Version : 00.90
  Creation Time : Tue Jul 27 15:16:33 2010
     Raid Level : raid5
     Array Size : 3903119872 (3722.31 GiB 3996.79 GB)
  Used Dev Size : 975779968 (930.58 GiB 999.20 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Fri Jul 30 11:00:59 2010
          State : clean, degraded
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : be5da881:eddef518:c28a7a3d:59ef3df7 (local to host testserver)
         Events : 0.12778

    Number   Major   Minor   RaidDevice State
       0       8       34        0      active sync   /dev/sdc2
       1       8       50        1      active sync   /dev/sdd2
       2       8       66        2      active sync   /dev/sde2
       3       0        0        3      removed
       4       0        0        4      removed

       5       8      194        -      spare   /dev/sdm2
       6       8       82        -      faulty spare   /dev/sdf2
```


And, if anyone cares, "hdparm -i /dev/sdf" gives me:
```
/dev/sdf:

 Model=WDC, FwRev=03.00C06, SerialNo=WD-WMATV5310411
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=32767kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

```


I've tried destroying and rebuilding the array -- zeroing the superblock and the whole deal -- several times, all with the exact same results as above.

All I want is a fresh Raid5 array with the five drives above -- I'm sure I'm just missing something stupid.  Any suggestions?

---

### Post by jacekk015 on 2010-07-30
mdadm works with RAID5 in that way that for 5 devices, it add 4 drives and sync then last fifth device.

In your example something is going wrong because sdf is making problems.

Try maybe for testing purpose to build 4 device RAID5 without sdf drive.

---

### Post by jahservant on 2010-07-30
jacekk015, the raid is building now without sdf; I'll you know what happens when it finishes.

---

### Post by jahservant on 2010-08-01
The Raid looks good with 4 drives:
```
root@testserver:~# mdadm --detail /dev/md2
/dev/md2:
        Version : 00.90
  Creation Time : Fri Jul 30 16:19:15 2010
     Raid Level : raid5
     Array Size : 2927339904 (2791.73 GiB 2997.60 GB)
  Used Dev Size : 975779968 (930.58 GiB 999.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Sun Aug  1 05:33:53 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 580cf8fe:ef4fbce6:c28a7a3d:59ef3df7 (local to host testserver)
         Events : 0.841

    Number   Major   Minor   RaidDevice State
       0       8       34        0      active sync   /dev/sdc2
       1       8       50        1      active sync   /dev/sdd2
       2       8       66        2      active sync   /dev/sde2
       3       8      194        3      active sync   /dev/sdm2

```


So I'm assuming this means sdf is a bad drive?  If I swap it out with a clean one, do I need to reconstruct the whole raid or can I change the raid level to five drives and add in the new one all at once?

Sorry for the noobish questions; I'm brand-new to software-based raids....

As a side note, the man entry for mdadm looks more like a novel than a helpful aid.  This may be a help for noobs to software raids: [http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/]("http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/")

---

### Post by jacekk015 on 2010-08-01
sdf - we cannot be sure for 100%
Sometimes it depends on disk. If it's a simple desktop drive it can have problem with TLER.
Response time.

You can always add drives and grow array, but you cannot shrink down number of devices.
All needed infos are in man mdadm.
mdadm --grow --help


For adding later sdf
```
mdadm --add /dev/md2 /dev/sdf
```It goes for spare, and then
```
mdadm --grow /dev/md2 --raid-devices=5
```Watch and enjoy
```
watch -n1 cat /proc/mdstat
```After all of this remember to go to /etc/mdadm/mdadm.conf and change number of devices for correct UUID. It doesn't make this automatically.

And always do backup ;-) RAID5 isn't safe to much. For example the moment [some hours] of growing or rebuilding because of bad disk.

---

### Post by rubylaser on 2010-08-02
You'll also need to grow the filesystem so that is can use the new space you gave it.
The filesystem the needs to be expanded to fill up the new space. For **EXT4** growth
umount your raid array then,
```
fsck.ext4 /dev/md2
resize2fs /dev/md2
```
For **XFS** growth
```
xfs_growfs /dev/md2
```

You can just run this to generate a new /etc/mdadm/mdadm.conf
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST [COLOR="Red"]fileserver[/COLOR]" >> /etc/mdadm/mdadm.conf
echo "MAILADDR [COLOR="Red"]root@localhost[/COLOR]" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Just replace the fileserver part in there with your machine's hostname, and the root@localhost with your email address.

---

### Post by hometoast on 2010-08-02
I similar looking issues to yours with my raid setup. Turned out to be a busted SATA port on the board. 

I'd try building the array while switching the cabling to eliminate that as an issue.

---

### Post by jahservant on 2010-08-05
thank you all for your help!

It looks like the raid is running fine now; so I'm calling it good enough ^_^

---

