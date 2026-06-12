---
title: "mdadm raid 5 issues - is this a two-drive failure?"
date: 2015-10-21
forum: Server Platforms
---

### Post by peter_london on 2015-10-21
Hello,

I'm worrying that my raid has run in degraded mode for a while, without me noticing it. I'm even more worried that the reason I'm now experiencing issues is because another drive has failed, but I'm not entirely sure yet. I would truly appreciate some help clearing this up!

First, let's examine all the drives and compare the "Update Time". I suppose this confirm that my /dev/sdb drive died on the 6th of October already?

[B]mdadm -E /dev/sdb1
[/B] ```

/dev/sdb1:          
           Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 50070e51:fdbd5a12:c3735ea2:7142fa9f
           Name : UBServer64bit:1  (local to host UBServer64bit)
  Creation Time : Sun Feb 15 22:41:22 2015
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
     Array Size : 5860268032 (5588.79 GiB 6000.91 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1fb350ed:024e28c3:b83566b3:4331dcc3


    Update Time : Tue Oct  6 04:53:53 2015
       Checksum : 1d56aecd - expected 1d56aecc
         Events : 185809


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing)
```
[B]mdadm -E /dev/sdc1
[/B]```
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 50070e51:fdbd5a12:c3735ea2:7142fa9f
           Name : UBServer64bit:1  (local to host UBServer64bit)
  Creation Time : Sun Feb 15 22:41:22 2015
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
     Array Size : 5860268032 (5588.79 GiB 6000.91 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ef17d264:2aa7600d:87fdabd6:5d7b9261


Internal Bitmap : 8 sectors from superblock
    Update Time : Wed Oct 21 18:16:44 2015
       Checksum : a01f23fd - correct
         Events : 260215


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : A.A ('A' == active, '.' == missing)
```
[B]mdadm -E /dev/sdd1
[/B]```
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x9
     Array UUID : 50070e51:fdbd5a12:c3735ea2:7142fa9f
           Name : UBServer64bit:1  (local to host UBServer64bit)
  Creation Time : Sun Feb 15 22:41:22 2015
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
     Array Size : 5860268032 (5588.79 GiB 6000.91 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e7894f86:06f29c88:1b1dc976:31d5e0ef


Internal Bitmap : 8 sectors from superblock
    Update Time : Wed Oct 21 18:16:44 2015
       Checksum : 6b445a45 - correct
         Events : 260215


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : A.A ('A' == active, '.' == missing)
```

I stopped the array earlier (was having boot up problems) so let's try to start it again :

[B]mdadm --assemble --scan -v
[/B]```
mdadm: looking for devices for /dev/md1


mdadm: /dev/sdd1 is identified as a member of /dev/md1, slot 2.
mdadm: /dev/sdc1 is identified as a member of /dev/md1, slot 0.
mdadm: /dev/sdb1 is identified as a member of /dev/md1, slot 1.
mdadm: added /dev/sdb1 to /dev/md1 as 1 (possibly out of date)
mdadm: added /dev/sdd1 to /dev/md1 as 2
mdadm: added /dev/sdc1 to /dev/md1 as 0
mdadm: /dev/md1 has been started with 2 drives (out of 3).
```

Ok, at least it started, but in degraded mode :

[B]mdadm --detail /dev/md1
[/B]```
/dev/md1:
        Version : 1.2
  Creation Time : Sun Feb 15 22:41:22 2015
     Raid Level : raid5
     Array Size : 5860268032 (5588.79 GiB 6000.91 GB)
  Used Dev Size : 2930134016 (2794.39 GiB 3000.46 GB)
   Raid Devices : 3
  Total Devices : 2
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Wed Oct 21 18:16:44 2015
          State : active, degraded 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : UBServer64bit:1  (local to host UBServer64bit)
           UUID : 50070e51:fdbd5a12:c3735ea2:7142fa9f
         Events : 260215


    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       0        0        1      removed
       3       8       49        2      active sync   /dev/sdd1
```

Looks promising. However, once I start trying to mount and access this array my system stops responding again. I found these nasty messages in the syslog :
```
Oct 21 18:16:16 UBServer64bit kernel: [ 8056.772460] md/raid:md1: read error not correctable (sector 3506701352 on sdd1).Oct 21 18:16:16 UBServer64bit kernel: [ 8056.772475] md/raid:md1: read error not correctable (sector 3506701360 on sdd1).
Oct 21 18:16:16 UBServer64bit kernel: [ 8056.772482] md/raid:md1: read error not correctable (sector 3506701368 on sdd1).
Oct 21 18:16:16 UBServer64bit kernel: [ 8056.772484] md/raid:md1: read error not correctable (sector 3506701376 on sdd1).
Oct 21 18:16:16 UBServer64bit kernel: [ 8056.772487] md/raid:md1: read error not correctable (sector 3506701384 on sdd1).
Oct 21 18:16:16 UBServer64bit kernel: [ 8056.772490] md/raid:md1: read error not correctable (sector 3506701392 on sdd1).
Oct 21 18:16:16 UBServer64bit kernel: [ 8056.772493] md/raid:md1: read error not correctable (sector 3506701400 on sdd1).
Oct 21 18:16:16 UBServer64bit kernel: [ 8056.772496] md/raid:md1: read error not correctable (sector 3506701408 on sdd1).
Oct 21 18:16:16 UBServer64bit kernel: [ 8056.772498] md/raid:md1: read error not correctable (sector 3506701416 on sdd1).
Oct 21 18:16:16 UBServer64bit kernel: [ 8056.772501] md/raid:md1: read error not correctable (sector 3506701424 on sdd1).
Oct 21 18:16:16 UBServer64bit kernel: [ 8056.772584] ata6: EH complete
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.830137] Buffer I/O error on device md1, logical block 876609797
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.832139] lost page write due to I/O error on md1
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.832399] Buffer I/O error on device md1, logical block 876609798
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.834187] lost page write due to I/O error on md1
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.834225] Buffer I/O error on device md1, logical block 876609799
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.835998] lost page write due to I/O error on md1
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.836031] Buffer I/O error on device md1, logical block 876609800
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.837753] lost page write due to I/O error on md1
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.837760] Buffer I/O error on device md1, logical block 876609801
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.839474] lost page write due to I/O error on md1
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.839479] Buffer I/O error on device md1, logical block 876609802
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.841179] lost page write due to I/O error on md1
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.841185] Buffer I/O error on device md1, logical block 876609803
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.842849] lost page write due to I/O error on md1
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.842854] Buffer I/O error on device md1, logical block 876609804
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.844515] lost page write due to I/O error on md1
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.844529] Buffer I/O error on device md1, logical block 876609805
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.846155] lost page write due to I/O error on md1
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.846160] Buffer I/O error on device md1, logical block 876609806
Oct 21 18:16:17 UBServer64bit kernel: [ 8056.847767] lost page write due to I/O error on md1
```

...amongst many others.

I assume this means that this array can't be saved, even with a new hard drive? Since I now have a two drive failure?

Is there anything else worth trying, or will I lose all my data? I should have the most critical stuff backuped. I think ;-).

Truly grateful for advice here, any ideas would be extremely appreciated. Thank you in advance!

Best regards

Peter

---

### Post by darkod on 2015-10-21
Yes, it doesn't look good, but it doesn't mean you should give up.

First of all, since you have backups, it depends on you if you think the time wasted to save the array (and it might not work) is worth it or not? If you prefer creating new array and restoring your backups that is one of the options.

sdb1 might have dropped out of whatever reason, and the disk could be good. The problem is it is out of date (as you noticed). You don't even need to compare dates, it's enough to compare the Events counter in --examine.

sdd1 errors don't look good and might mean failing disk. So even if you get the array going it might have corrupted data (one member out of date and one failing).

So, you wanna try and see if you can save it or not? It will be good practice too, even if you have backups. But you might not have the time. :)

---

### Post by peter_london on 2015-10-21
Hey there darkod, thanks for your reply! I have all the time in the world for this and I'm definitely up for trying to save the data :). I suppose I have to buy two new 3TB hard drives. I will order these today already. What's my next step? This is gonna be interesting :).

---

### Post by darkod on 2015-10-21
Here is a basic guide from a forum member that knows mdadm raid: [http://zackreed.me/articles/50-recovery-from-a-multiple-disk-failure-with-mdadm](http://zackreed.me/articles/50-recovery-from-a-multiple-disk-failure-with-mdadm)

Basically, the first step would be to force the assemble, and if that doesn't work, to add the run option. In any case don't forget to stop the array if it's currently active (you might need to unmount it first if it's mounted). In any case, just try to assemble it and leave it alone until it rebuilds. Don't try to mount it and use it, so that it has as little load as possible until it finishes the rebuild.

Option 1:
```
sudo mdadm --stop /dev/md1
sudo mdadm --assemble --force --verbose /dev/md1 /dev/sd[cbd]1
```

Option 2:
```
sudo mdadm --stop /dev/md1
sudo mdadm --assemble --force --run --verbose /dev/md1 /dev/sd[cbd]1
```

According to your --examine the order of the partitions is sdc1-sdb1-sdd1, that's why I'm using /dev/sd[cbd]1 as the order in --assemble.

Lets see how that goes.

PS. If you use sudo -i and run the commands as root drop the sudo in front of each command of course.

---

### Post by peter_london on 2015-10-21
Alright, thanks darkrod. I tried option 1 :

```
mdadm --assemble --force --verbose /dev/md1 /dev/sd[cbd]1mdadm: looking for devices for /dev/md1
mdadm: /dev/sdb1 is identified as a member of /dev/md1, slot 1.
mdadm: /dev/sdc1 is identified as a member of /dev/md1, slot 0.
mdadm: /dev/sdd1 is identified as a member of /dev/md1, slot 2.
mdadm: added /dev/sdb1 to /dev/md1 as 1 (possibly out of date)
mdadm: added /dev/sdd1 to /dev/md1 as 2
mdadm: added /dev/sdc1 to /dev/md1 as 0
mdadm: /dev/md1 has been started with 2 drives (out of 3).
```

Looks like the same result as I got with the "mdadm --assemble --scan -v" command though?

Just for info, earlier today I already tried to force the assemble, because otherwise it would just give error messages. Either because of busy drives or I/O error, if I remember correctly. And I also think all my 3 drives were being marked as spares in /cat/mdstat. I stopped the raid and forced the assemble, and it finally assembled, but in degraded mode. I even tried mounting it once and it worked, but once trying to access the disk the system stopped responding. I never tried the --run parameter though - would it make any difference to try?

EDIT : I checked the link you posted. Is this the next thing I should try :

```
mdadm --create --assume-clean /dev/md0 /dev/sd[cbd]1
```

?

Some fresh info (although I believe it's the same as above) : 

```
cat /proc/mdstatPersonalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdc1[0] sdd1[3]
      5860268032 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [U_U]
      bitmap: 22/22 pages [88KB], 65536KB chunk


unused devices: <none>
```

```
mdadm --detail /dev/md1/dev/md1:
        Version : 1.2
  Creation Time : Sun Feb 15 22:41:22 2015
     Raid Level : raid5
     Array Size : 5860268032 (5588.79 GiB 6000.91 GB)
  Used Dev Size : 2930134016 (2794.39 GiB 3000.46 GB)
   Raid Devices : 3
  Total Devices : 2
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Wed Oct 21 22:53:26 2015
          State : active, degraded 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : UBServer64bit:1  (local to host UBServer64bit)
           UUID : 50070e51:fdbd5a12:c3735ea2:7142fa9f
         Events : 260223


    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       0        0        1      removed
       3       8       49        2      active sync   /dev/sdd1
```

[B]dmesg 
[/B]
```

[   16.223441] md: bind<sdb1>
[   16.231534] md: bind<sdd1>
[   16.243852] md: bind<sdc1>
[   16.248551] md: kicking non-fresh sdb1 from array!
[   16.248563] md: unbind<sdb1>
[   16.272199] md: export_rdev(sdb1)
[   16.273728] md/raid:md1: device sdc1 operational as raid disk 0
[   16.273732] md/raid:md1: device sdd1 operational as raid disk 2
[   16.274157] md/raid:md1: allocated 0kB
[   16.274246] md/raid:md1: raid level 5 active with 2 out of 3 devices, algorithm 2
[   16.274296] RAID conf printout:
[   16.274297]  --- level:5 rd:3 wd:2
[   16.274300]  disk 0, o:1, dev:sdc1
[   16.274302]  disk 2, o:1, dev:sdd1
[   16.274408] created bitmap (22 pages) for device md1
[   16.275220] md1: bitmap initialized from disk: read 2 pages, set 2845 of 44711 bits
[   16.276310] md1: detected capacity change from 0 to 6000914464768
[   16.288910]  md1: unknown partition table
[   16.536039] usb 5-1: new full-speed USB device number 4 using uhci_hcd
[   16.737793] usb 5-1: New USB device found, idVendor=05ac, idProduct=8205
[   16.737800] usb 5-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   16.757826] Bluetooth: Core ver 2.17
[   16.757862] NET: Registered protocol family 31
[   16.757865] Bluetooth: HCI device and connection manager initialized
[   16.758627] Bluetooth: HCI socket layer initialized
[   16.758632] Bluetooth: L2CAP socket layer initialized
[   16.758639] Bluetooth: SCO socket layer initialized
[   16.762179] usbcore: registered new interface driver btusb
[   18.259811] sky2 0000:01:00.0 eth0: Link is up at 1000 Mbps, full duplex, flow control both
[   18.259831] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.762834] ata6.02: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   23.762876] ata6.02: irq_stat 0x00060002, device error via D2H FIS
[   23.762913] ata6.02: failed command: READ DMA EXT
[   23.762943] ata6.02: cmd 25/00:c0:40:09:a4/00:02:d0:00:00/e0 tag 6 dma 360448 in
[   23.762943]          res 51/04:c0:40:09:a4/00:02:d0:00:00/e0 Emask 0x1 (device error)
[   23.763021] ata6.02: status: { DRDY ERR }
[   23.763046] ata6.02: error: { ABRT }
[   23.764447] ata6.02: configured for UDMA/100
[   23.764629] ata6: EH complete
[   28.622183] Buffer I/O error on device md1, logical block 876609797
[   28.622228] lost page write due to I/O error on md1
[   28.622238] Buffer I/O error on device md1, logical block 876609798
[   28.622272] lost page write due to I/O error on md1
[   28.622276] Buffer I/O error on device md1, logical block 876609799
[   28.622309] lost page write due to I/O error on md1
[   28.622313] Buffer I/O error on device md1, logical block 876609800
[   28.622346] lost page write due to I/O error on md1
[   28.622350] Buffer I/O error on device md1, logical block 876609801
[   28.622383] lost page write due to I/O error on md1
[   28.622387] Buffer I/O error on device md1, logical block 876609802
[   28.622420] lost page write due to I/O error on md1
[   28.622424] Buffer I/O error on device md1, logical block 876609803
[   28.622457] lost page write due to I/O error on md1
[   28.622463] Buffer I/O error on device md1, logical block 876609804
[   28.622496] lost page write due to I/O error on md1
[   28.622500] Buffer I/O error on device md1, logical block 876609805
[   28.622533] lost page write due to I/O error on md1
[   28.622537] Buffer I/O error on device md1, logical block 876609806
[   28.622570] lost page write due to I/O error on md1
[   32.032958] ata6.02: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   32.034216] ata6.02: irq_stat 0x00060002, device error via D2H FIS
[   32.035330] ata6.02: failed command: READ DMA EXT
[   32.036485] ata6.02: cmd 25/00:00:20:08:04/00:04:d1:00:00/e0 tag 1 dma 524288 in
[   32.036485]          res 51/04:00:20:08:04/00:04:d1:00:00/e0 Emask 0x1 (device error)
[   32.038819] ata6.02: status: { DRDY ERR }
[   32.039983] ata6.02: error: { ABRT }
[   32.042549] ata6.02: configured for UDMA/100
[   32.042744] ata6: EH complete
[   38.044781] ata6.02: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   38.046173] ata6.02: irq_stat 0x00060002, device error via D2H FIS
[   38.047366] ata6.02: failed command: READ DMA EXT
[   38.048571] ata6.02: cmd 25/00:00:20:08:04/00:04:d1:00:00/e0 tag 4 dma 524288 in
[   38.048571]          res 51/04:00:20:08:04/00:04:d1:00:00/e0 Emask 0x1 (device error)
[   38.050984] ata6.02: status: { DRDY ERR }
[   38.052215] ata6.02: error: { ABRT }
[   38.054832] ata6.02: configured for UDMA/100
[   38.055025] ata6: EH complete
[   41.101135] ata6.02: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   41.102471] ata6.02: irq_stat 0x00060002, device error via D2H FIS
[   41.103723] ata6.02: failed command: READ DMA EXT
[   41.105000] ata6.02: cmd 25/00:00:20:08:04/00:04:d1:00:00/e0 tag 7 dma 524288 in
[   41.105000]          res 51/04:00:20:08:04/00:04:d1:00:00/e0 Emask 0x1 (device error)
[   41.107583] ata6.02: status: { DRDY ERR }
[   41.108903] ata6.02: error: { ABRT }
[   41.111610] ata6.02: configured for UDMA/100
[   41.111804] ata6: EH complete
[   45.306153] ata6.02: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   45.307509] ata6.02: irq_stat 0x00060002, device error via D2H FIS
[   45.308872] ata6.02: failed command: READ DMA EXT
[   45.310229] ata6.02: cmd 25/00:00:20:08:04/00:04:d1:00:00/e0 tag 10 dma 524288 in
[   45.310229]          res 51/04:00:20:08:04/00:04:d1:00:00/e0 Emask 0x1 (device error)
[   45.313016] ata6.02: status: { DRDY ERR }
[   45.314425] ata6.02: error: { ABRT }
[   45.317169] ata6.02: configured for UDMA/100
[   45.317332] ata6: EH complete
[   50.494899] ata6.02: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   50.496530] ata6.02: irq_stat 0x00060002, device error via D2H FIS
[   50.497971] ata6.02: failed command: READ DMA EXT
[   50.499421] ata6.02: cmd 25/00:00:20:08:04/00:04:d1:00:00/e0 tag 12 dma 524288 in
[   50.499421]          res 51/04:00:20:08:04/00:04:d1:00:00/e0 Emask 0x1 (device error)
[   50.502416] ata6.02: status: { DRDY ERR }
[   50.503916] ata6.02: error: { ABRT }
[   50.506852] ata6.02: configured for UDMA/100
[   50.507045] ata6: EH complete
[   53.854417] ata6.02: limiting SATA link speed to 1.5 Gbps
[   53.854589] ata6.02: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[   53.856311] ata6.02: irq_stat 0x00060002, device error via D2H FIS
[   53.857839] ata6.02: failed command: READ DMA EXT
[   53.859361] ata6.02: cmd 25/00:00:20:08:04/00:04:d1:00:00/e0 tag 13 dma 524288 in
[   53.859361]          res 51/04:00:20:08:04/00:04:d1:00:00/e0 Emask 0x1 (device error)
[   53.862475] ata6.02: status: { DRDY ERR }
[   53.864036] ata6.02: error: { ABRT }
[   53.865768] ata6.02: hard resetting link
[   54.184971] ata6.02: SATA link up 3.0 Gbps (SStatus 123 SControl 310)
[   54.186311] ata6.02: configured for UDMA/100
[   54.186535] sd 5:2:0:0: [sdd]  
[   54.186538] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   54.186540] sd 5:2:0:0: [sdd]  
[   54.186542] Sense Key : Aborted Command [current] [descriptor]
[   54.186546] Descriptor sense data with sense descriptors (in hex):
[   54.186548]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   54.186557]         d1 04 08 20 
[   54.186561] sd 5:2:0:0: [sdd]  
[   54.186563] Add. Sense: No additional sense information
[   54.186565] sd 5:2:0:0: [sdd] CDB: 
[   54.186567] Read(16): 88 00 00 00 00 00 d1 04 08 20 00 00 04 00 00 00
[   54.186578] end_request: I/O error, dev sdd, sector 3506702368
[   54.188162] md/raid:md1: read error not correctable (sector 3506700320 on sdd1).
[   54.188169] md/raid:md1: read error not correctable (sector 3506700328 on sdd1).
[   54.188171] md/raid:md1: read error not correctable (sector 3506700336 on sdd1).
[   54.188174] md/raid:md1: read error not correctable (sector 3506700344 on sdd1).
[   54.188176] md/raid:md1: read error not correctable (sector 3506700352 on sdd1).
[   54.188179] md/raid:md1: read error not correctable (sector 3506700360 on sdd1).
[   54.188182] md/raid:md1: read error not correctable (sector 3506700368 on sdd1).
[   54.188185] md/raid:md1: read error not correctable (sector 3506700376 on sdd1).
[   54.188187] md/raid:md1: read error not correctable (sector 3506700384 on sdd1).
[   54.188190] md/raid:md1: read error not correctable (sector 3506700392 on sdd1).
[   54.188271] ata6: EH complete
[   58.497281] ata6.02: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   58.498947] ata6.02: irq_stat 0x00060002, device error via D2H FIS
[   58.500540] ata6.02: failed command: READ DMA EXT
[   58.502110] ata6.02: cmd 25/00:00:20:08:04/00:04:d1:00:00/e0 tag 19 dma 524288 in
[   58.502110]          res 51/04:00:20:08:04/00:04:d1:00:00/e0 Emask 0x1 (device error)
[   58.505295] ata6.02: status: { DRDY ERR }
[   58.506876] ata6.02: error: { ABRT }
[   58.509849] ata6.02: configured for UDMA/100
[   58.510042] ata6: EH complete
[   61.879201] ata6.02: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   61.880998] ata6.02: irq_stat 0x00060002, device error via D2H FIS
[   61.882620] ata6.02: failed command: READ DMA EXT
[   61.884265] ata6.02: cmd 25/00:00:20:08:04/00:04:d1:00:00/e0 tag 21 dma 524288 in
[   61.884265]          res 51/04:00:20:08:04/00:04:d1:00:00/e0 Emask 0x1 (device error)
[   61.887624] ata6.02: status: { DRDY ERR }
[   61.889333] ata6.02: error: { ABRT }
[   61.892462] ata6.02: configured for UDMA/100
[   61.892645] ata6: EH complete
[  130.832096] usb 1-6: new high-speed USB device number 5 using ehci-pci
[  130.972909] usb 1-6: New USB device found, idVendor=05ac, idProduct=1006
[  130.972919] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  130.972925] usb 1-6: Product: Keyboard Hub
[  130.972930] usb 1-6: Manufacturer: Apple, Inc.
[  130.972935] usb 1-6: SerialNumber: 000000000000
[  130.973292] hub 1-6:1.0: USB hub found
[  130.973373] hub 1-6:1.0: 3 ports detected
[  131.244169] usb 1-6.2: new low-speed USB device number 6 using ehci-pci
[  131.342914] usb 1-6.2: New USB device found, idVendor=05ac, idProduct=0221
[  131.342924] usb 1-6.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  131.342930] usb 1-6.2: Product: Apple Keyboard
[  131.342935] usb 1-6.2: Manufacturer: Apple, Inc
[  131.359292] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6.2/1-6.2:1.0/input/input9
[  131.359738] apple 0003:05AC:0221.0004: input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc Apple Keyboard] on usb-0000:00:1d.7-6.2/input0
[  131.360843] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6.2/1-6.2:1.1/input/input10
[  131.361026] apple 0003:05AC:0221.0005: input,hidraw1: USB HID v1.11 Device [Apple, Inc Apple Keyboard] on usb-0000:00:1d.7-6.2/input1
[  141.378897] init: mountall main process (220) terminated with status 2
[  184.502005] md1: detected capacity change from 6000914464768 to 0
[  184.502012] md: md1 stopped.
[  184.502026] md: unbind<sdc1>
[  184.516095] md: export_rdev(sdc1)
[  184.516136] md: unbind<sdd1>
[  184.524082] md: export_rdev(sdd1)
[  196.964593] init: mountall main process (1074) terminated with status 2
[  222.204602] RPC: Registered named UNIX socket transport module.
[  222.204606] RPC: Registered udp transport module.
[  222.204608] RPC: Registered tcp transport module.
[  222.204610] RPC: Registered tcp NFSv4.1 backchannel transport module.
[  222.224598] FS-Cache: Netfs 'nfs' registered for caching
[  222.273972] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[  222.363758] init: plexmediaserver main process (1426) terminated with status 1
[  222.363777] init: plexmediaserver main process ended, respawning
[  222.444806] init: failsafe main process (1413) killed by TERM signal
[  222.451630] init: plexmediaserver main process (1497) terminated with status 1
[  222.451646] init: plexmediaserver main process ended, respawning
[  222.538050] init: plexmediaserver main process (1512) terminated with status 1
[  222.538559] init: plexmediaserver main process ended, respawning
[  222.562195] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  222.562200] Bluetooth: BNEP filters: protocol multicast
[  222.562216] Bluetooth: BNEP socket layer initialized
[  222.593123] Bluetooth: RFCOMM TTY layer initialized
[  222.593142] Bluetooth: RFCOMM socket layer initialized
[  222.593149] Bluetooth: RFCOMM ver 1.11
[  222.635768] init: plexmediaserver main process (1589) terminated with status 1
[  222.635785] init: plexmediaserver main process ended, respawning
[  222.698735] init: plexmediaserver main process (1612) terminated with status 1
[  222.698755] init: plexmediaserver main process ended, respawning
[  222.757362] init: plexmediaserver main process (1633) terminated with status 1
[  222.757380] init: plexmediaserver main process ended, respawning
[  222.819056] init: plexmediaserver main process (1683) terminated with status 1
[  222.819073] init: plexmediaserver main process ended, respawning
[  222.854943] init: plexmediaserver main process (1713) terminated with status 1
[  222.854960] init: plexmediaserver main process ended, respawning
[  222.963652] init: plexmediaserver main process (1717) terminated with status 1
[  222.963675] init: plexmediaserver main process ended, respawning
[  223.112718] init: plexmediaserver main process (1837) terminated with status 1
[  223.112736] init: plexmediaserver main process ended, respawning
[  223.202401] init: plexmediaserver main process (1899) terminated with status 1
[  223.202418] init: plexmediaserver respawning too fast, stopped
[  337.459281] md: md1 stopped.
[  346.448667] md: md1 stopped.
[  346.501687] md: bind<sdb1>
[  346.502237] md: bind<sdd1>
[  346.529155] md: bind<sdc1>
[  346.529227] md: kicking non-fresh sdb1 from array!
[  346.529237] md: unbind<sdb1>
[  346.544060] md: export_rdev(sdb1)
[  346.549047] md/raid:md1: device sdc1 operational as raid disk 0
[  346.549052] md/raid:md1: device sdd1 operational as raid disk 2
[  346.549546] md/raid:md1: allocated 0kB
[  346.549582] md/raid:md1: raid level 5 active with 2 out of 3 devices, algorithm 2
[  346.549640] RAID conf printout:
[  346.549642]  --- level:5 rd:3 wd:2
[  346.549644]  disk 0, o:1, dev:sdc1
[  346.549646]  disk 2, o:1, dev:sdd1
[  346.549761] created bitmap (22 pages) for device md1
[  346.550539] md1: bitmap initialized from disk: read 2 pages, set 2845 of 44711 bits
[  346.550840] md1: detected capacity change from 0 to 6000914464768
[  346.559210]  md1: unknown partition table

```

---

### Post by darkod on 2015-10-21
Hmmm, I can't be 100% sure but I think it's worth trying the --run option. If I'm not mistaken, the --force does not actually try to activate the out of date member (hence sdb1 still says out of date and not part of the array). The --run should force it to be included in the array.

Note that some data might get corrupted by forcing this out of date member into the array, but once you have it there, and assuming sdb and sdc are good, you will have at least two good members so even if sdd is failing, it would not matter. That's my line of thought at least...

So, try stopping the array again and do the option with --run. See if it changes anything.

---

### Post by peter_london on 2015-10-21
Cheers darkrod & thank you so much for helping me with this :).

Seems like it gives the same result?

```
sudo mdadm --assemble --force --run --verbose /dev/md1 /dev/sd[cbd]1mdadm: looking for devices for /dev/md1
mdadm: /dev/sdb1 is identified as a member of /dev/md1, slot 1.
mdadm: /dev/sdc1 is identified as a member of /dev/md1, slot 0.
mdadm: /dev/sdd1 is identified as a member of /dev/md1, slot 2.
mdadm: added /dev/sdb1 to /dev/md1 as 1 (possibly out of date)
mdadm: added /dev/sdd1 to /dev/md1 as 2
mdadm: added /dev/sdc1 to /dev/md1 as 0
mdadm: /dev/md1 has been started with 2 drives (out of 3).
```

Should we give this a shot, perhaps :

```
[COLOR=#000000][FONT=Ubuntu Mono]mdadm --create --assume-clean /dev/md0 /dev/sd[cbd]1[/FONT][/COLOR]
```

---

### Post by darkod on 2015-10-21
Well, not you don't have much option except the --create --assume-clean. That's the last one but you tried everything else.

To try that you will have to zero the superblocks as per that tutorial. Also what I am worried about is that sdb1 is quite out of date and it might corrupt some data if we let mdadm "think" that all three partitions are up to date when they are not. You have the option to try the --create with only sdc1 and sdd1 but in this case I am also worried that sdd1 might be failing on you, so we can't predict if using only sdc1 and sdd1 won't also corrupt some data.

So, first is zeroing the superblocks. After that you have two options, --create with 2 members or with 3. If creating with 2 members works and sdd does not mess things up, adding sdb later will "eliminate" the out of date problem because the array will already be assembled from sdc1 and sdd1 which have up to date data, and on adding sdb1 it will sync according to current sdc1-sdd1 status, not according to the data sdb1 has on it. Am I making sense???

So, it would be something like:
```
mdadm --stop /dev/md1 (or /dev/md0 depending which one you used)
mdadm --zero-superblock /dev/sdb1
mdadm --zero-superblock /dev/sdc1
mdadm --zero-superblock /dev/sdd1
```

After that, according to the decision you make:
option 1
```
mdadm --create --assume-clean --verbose /dev/md1 /dev/sdc1 missing /dev/sdd1
```

or option 2
```
mdadm --create --assume-clean --verbose /dev/md1 /dev/sd[cbd]1
```

In any case, as we discussed, I think it's better to leave the array to fully sync before trying to mount and use it. No need to create additional load while it's still syncing.

---

### Post by peter_london on 2015-10-22
Yes darkrod, you make perfect sense :).

Can't chose between the two options though. If you had to pick one of them - which one would you pick? :D

---

### Post by darkod on 2015-10-22
You said you have backups right? Fairly recent?

In such case, I would select option 1, but in fact I would adjust the command little, just to make sure correct raid level is created. Like this:
```
mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=3 /dev/md1 /dev/sdc1 missing /dev/sdd1
```

With little luck, that should assemble sdc1-sdd1 and one missing member using the existing up-to-date data on them. Once the array is synced, you will add sdb1 to the array.

---

### Post by peter_london on 2015-10-22
> **darkod said:**
> You said you have backups right? Fairly recent?

Yes, I'm backing up the most important stuff to the cloud (crashplan) so no worries there :). I know that I have the critical stuff there. However, it still would be nice to be able to access the less critical stuff as well... That's why I want to do this. And also because it's a fun experiment of course :).

> **darkod said:**
> 
In such case, I would select option 1, but in fact I would adjust the command little, just to make sure correct raid level is created. Like this:
```
mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=3 /dev/md1 /dev/sdc1 missing /dev/sdd1
```

With little luck, that should assemble sdc1-sdd1 and one missing member using the existing up-to-date data on them. Once the array is synced, you will add sdb1 to the array.

Cool, I'll try this now and I'll post the results :)

---

### Post by peter_london on 2015-10-22
Looks good so far I believe? What's next? :D

EDIT : Or maybe not so good.... Size and mtime looks a little bit strange :P

```

root@UBServer64bit:~# mdadm --zero-superblock /dev/sdb1
root@UBServer64bit:~# mdadm --zero-superblock /dev/sdc1
root@UBServer64bit:~# mdadm --zero-superblock /dev/sdd1
root@UBServer64bit:~# mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=3 /dev/md1 /dev/sdc1 missing /dev/sdd1
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: /dev/sdc1 appears to contain an ext2fs file system
    size=-1364702208K  mtime=Thu Jan  1 01:00:00 1970
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=-1364702208K  mtime=Thu Jan  1 01:00:00 1970
mdadm: size set to 2930133504K
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md1 started.
root@UBServer64bit:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdd1[2] sdc1[0]
      5860267008 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [U_U]
      
unused devices: <none>
root@UBServer64bit:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdd1[2] sdc1[0]
      5860267008 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [U_U]
      
unused devices: <none>

```

However, mdadm --detail gives more hopeful info :)

```

mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Thu Oct 22 23:17:24 2015
     Raid Level : raid5
     Array Size : 5860267008 (5588.79 GiB 6000.91 GB)
  Used Dev Size : 2930133504 (2794.39 GiB 3000.46 GB)
   Raid Devices : 3
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Thu Oct 22 23:17:24 2015
          State : clean, degraded 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : UBServer64bit:1  (local to host UBServer64bit)
           UUID : c97b862f:891b66c8:90be8fb2:7c997650
         Events : 0


    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       0        0        1      removed
       2       8       49        2      active sync   /dev/sdd1

```

```

Model: ATA H/W DISK 1 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name      Flags
 1      1049kB  3001GB  3001GB  ext4         Intenso1  raid




Model: ATA H/W DISK 2 (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  3001GB  3001GB  ext4         Verb3tb  raid




Model: ATA H/W DISK 3 (scsi)
Disk /dev/sdd: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name      Flags
 1      1049kB  3001GB  3001GB  ext4         Intenso2  raid

Error: /dev/md1: unrecognised disk label          

```

---

### Post by darkod on 2015-10-22
I completely forgot --assume-clean does not do the initial sync, so there was no sync to start right away.

Can you post the mdadm --detail /dev/md1 now? To check details...

---

### Post by peter_london on 2015-10-22
```

mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Thu Oct 22 23:17:24 2015
     Raid Level : raid5
     Array Size : 5860267008 (5588.79 GiB 6000.91 GB)
  Used Dev Size : 2930133504 (2794.39 GiB 3000.46 GB)
   Raid Devices : 3
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Thu Oct 22 23:17:24 2015
          State : clean, degraded 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : UBServer64bit:1  (local to host UBServer64bit)
           UUID : c97b862f:891b66c8:90be8fb2:7c997650
         Events : 0


    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       0        0        1      removed
       2       8       49        2      active sync   /dev/sdd1

```

---

### Post by darkod on 2015-10-22
OK, lets try to add sdb1 now:
```
mdadm /dev/md1 --add /dev/sdb1
```

That should start a sync process if you check with cat /proc/mdstat.

---

### Post by peter_london on 2015-10-22
Correct!

```

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdb1[3] sdd1[2] sdc1[0]
      5860267008 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [U_U]
      [>....................]  recovery =  0.1% (4406912/2930133504) finish=1146.5min speed=42530K/sec
      
unused devices: <none>

```

Thank you for everything darkod! I will post the results when I have them ( in a few days :P)

Cheers!

---

### Post by darkod on 2015-10-22
No problem. The only worry at this point is if sdd is failing whether it will "stay alive" long enough for the sync to finish. And whether the data on it is clean or partly corrupted. Once the sync is finished and sdb1 is full member of the array, you don't need sdd any more and you can consider replacing it with a new HDD. But lets wait out the sync first...

---

### Post by peter_london on 2015-10-23
Looks like it failed :

```

mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Thu Oct 22 23:17:24 2015
     Raid Level : raid5
     Array Size : 5860267008 (5588.79 GiB 6000.91 GB)
  Used Dev Size : 2930133504 (2794.39 GiB 3000.46 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent


    Update Time : Fri Oct 23 07:55:05 2015
          State : clean, FAILED 
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1


         Layout : left-symmetric
     Chunk Size : 512K


           Name : UBServer64bit:1  (local to host UBServer64bit)
           UUID : c97b862f:891b66c8:90be8fb2:7c997650
         Events : 104


    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       0        0        1      removed
       2       0        0        2      removed


       2       8       49        -      faulty spare   /dev/sdd1
       3       8       17        -      spare   /dev/sdb1

```

Apparently, it went up to 42.5% before it failed :

```


This is an automatically generated mail message from mdadm
running on UBServer64bit


A Fail event had been detected on md device /dev/md1.


It could be related to component device /dev/sdd1.


Faithfully yours, etc.


P.S. The /proc/mdstat file currently contains the following:


Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdb1[3] sdd1[2](F) sdc1[0]
     5860267008 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/1] [U__]
     [========>............]  recovery = 42.5% (1246501508/2930133504) finish=147740.6min speed=189K/sec


unused devices: <none>

```

Wish I had set up the e-mail notifications properly a little earlier :).

I suppose there is nothing else to do here? Except to buy at least one more hardrive and restore the backup. my /dev/sdb disk could still be good, right? /dev/sdd goes in the trash though :D

Cheers

Peter

---

### Post by darkod on 2015-10-24
It seems so. There is no reason to suspect sdb (yet). So, buy one disk for a start and create new raid5 array and restore your backup. You will probably need to zero the superblocks on sdb1 and sdc1 so that mdadm doesn't complain adding them to a new array.

---

### Post by rubylaser on 2015-10-24
Another option is to use gddrescue on the failing disk to recover to a new disk.  This will try harder to recover the data on the failing disk.  If the recovery works, you can try to add the new disk as darkod mentioned above.  But, if you have a good backup, I'd zero the superblocks on all of the disks, run badblocks -wsv on each of the disks (this will wipe out any data on the disks) followed by smartctl to check if the counters have increased to make sure all of them are healthly, and finally, build a new array.

---

