---
title: "Help with RAID 10 failure"
date: 2008-10-05
forum: Server Platforms
---

### Post by shieldw0lf on 2008-10-05
Hi everyone,

I've got a LAPP server that I'm running in a RAID 10 set up, and I got a dreadful email today:

---//---

This is an automatically generated mail message from mdadm
running on xyz.com

A Fail event had been detected on md device /dev/md1.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sdc2[0] sdd2[1]
      78123968 blocks [2/2] [UU]
      [>....................]  check =  4.8% (3813952/78123968) finish=17.5min speed=70626K/sec
      
md0 : active raid1 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      497856 blocks [4/4] [UUUU]
      
md1 : active raid1 sda2[2](F) sdb2[1]
      78123968 blocks [2/1] [_U]
      
unused devices: <none>

---//---

I've got 4 80G Serial ATA drives installed.  I made a small RAID1 across all 4 disks and put my boot partition in it, 4 swap partitions and two 75G mirrors, which I'm striping across into a 150G volume.

cat /proc/mdstat gives me the following:

---//---

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sdc2[0] sdd2[1]
      78123968 blocks [2/2] [UU]
      
md0 : active raid1 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      497856 blocks [4/4] [UUUU]
      
md1 : active raid1 sda2[2](F) sdb2[1]
      78123968 blocks [2/1] [_U]
      
unused devices: <none>

---//---

I set this up quite a long time ago, and I've never had it fail, so I'm not sure what to do.  It's still running, and I've backed up all my databases, /var/www and /etc.  

At this point, I'm not sure if I just need to rebuild my array, or if I need to replace the disk, and I don't know how I would find out.  If someone can get me started, I'd appreciate it.

Cheers

---

### Post by fjgaude on 2008-10-05
Well, one thing to do is:

```
sudo mdadm -D /dev/md[n]
```

That should show which of the drive(s) are failed. Then you can find out which physical drive relates to which:

```
sudo hdparm -i -v /dev/sd[nn]
```

Shows the SN versus the drive name, plus more.

I don't know if you have hot replacement type of drives or not. Normally you would simply fault the drive, remove it then add one back using mdadm.

```
sudo mdadm /dev/md32 -f  or -r  or  -a  /dev/sd[nn]
```

You are likely rebuilding automatically now with the bad drive(s) in place.

It would be good to study the **man mdadm** pages and these:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
 /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
 [http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

Let us know how you are doing.

---

### Post by shieldw0lf on 2008-10-06
Well, I've read through everything.  This is my developing-business-on-the-side server and I had to go to work-that-pays-the-rent, so I haven't gotten down to the shop to get another drive yet and the machine is still running in degraded mode.

I got the following details from mdadm and hdparm:

```
me@xyz.com:/dev$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Mon Jun 18 19:00:27 2007
     Raid Level : raid1
     Array Size : 497856 (486.27 MiB 509.80 MB)
  Used Dev Size : 497856 (486.27 MiB 509.80 MB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Oct  6 08:04:58 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

           UUID : 4a831960:8bd4ca1f:63efb40a:23cdc426
         Events : 0.82

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1

me@xyz.com/dev$ sudo mdadm -D /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Mon Jun 18 19:00:40 2007
     Raid Level : raid1
     Array Size : 78123968 (74.50 GiB 80.00 GB)
  Used Dev Size : 78123968 (74.50 GiB 80.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Mon Oct  6 17:23:25 2008
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0

           UUID : a5f93aa7:df06eb7a:559d9ae9:69ac1996
         Events : 0.93661

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       18        1      active sync   /dev/sdb2

       2       8        2        -      faulty spare   /dev/sda2


me@xyz.com:/dev$ sudo mdadm -D /dev/md2
/dev/md2:
        Version : 00.90.03
  Creation Time : Mon Jun 18 19:00:48 2007
     Raid Level : raid1
     Array Size : 78123968 (74.50 GiB 80.00 GB)
  Used Dev Size : 78123968 (74.50 GiB 80.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Mon Oct  6 17:23:37 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : f5a29baa:c4fd24f1:b1c98eef:446650f1
         Events : 0.97

    Number   Major   Minor   RaidDevice State
       0       8       34        0      active sync   /dev/sdc2
       1       8       50        1      active sync   /dev/sdd2


me@xyz.com:/dev$ sudo hdparm -i -v /dev/sda

/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 10011/255/63, sectors = 160836480, start = 0

 Model=Hitachi HDS721680PLA380                 , FwRev=P21OAB3A, SerialNo=      PVB100Z1SHAD1F
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=52
 BuffType=DualPortCache, BuffSize=7384kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=160836480
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 1:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode

me@xyz.com:/dev$ sudo hdparm -i -v /dev/sdb

/dev/sdb:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 10011/255/63, sectors = 160836480, start = 0

 Model=Hitachi HDS721680PLA380                 , FwRev=P21OAB3A, SerialNo=      PVB100Z1SKGZ1F
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=52
 BuffType=DualPortCache, BuffSize=7384kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=160836480
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 1:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode

me@xyz.com:/dev$ sudo hdparm -i -v /dev/sdc

/dev/sdc:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 10011/255/63, sectors = 160836480, start = 0

 Model=Hitachi HDS721680PLA380                 , FwRev=P21OAB3A, SerialNo=      PVB100Z1SHTN4F
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=52
 BuffType=DualPortCache, BuffSize=7384kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=160836480
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 1:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode

me@xyz.com:/dev$ sudo hdparm -i -v /dev/sdd

/dev/sdd:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 10011/255/63, sectors = 160836480, start = 0

 Model=Hitachi HDS721680PLA380                 , FwRev=P21OAB3A, SerialNo=      PVB100Z1SE439F
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=52
 BuffType=DualPortCache, BuffSize=7384kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=160836480
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 1:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode

me@xyz.com:/dev$ 


```

I think I understand how to do the swap and rebuild; I'll let you guys know how it pans out once I get another drive.

---

### Post by fjgaude on 2008-10-06
Looks like you wish to take out the sdb, SN=PVB100Z1SKGZ1F, drive, eh?

Yes, let us know how you make out.

---

