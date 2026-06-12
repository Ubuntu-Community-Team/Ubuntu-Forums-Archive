---
title: "mdadm raid 5 grow process interupted by drive issues"
date: 2009-07-16
forum: Server Platforms
---

### Post by Xaga on 2009-07-16
Something has caused 2 discs that I was adding to a raid 5 to go faulty during the grow. I do not have a backup file for the grow session as I forgot that it existed and when I realized that it was missing, I had already started the grow. Everything seemd to be going fine for about a day and a half, and then something goes wrong. When I check on it, it has stopped reshaping, and the I have the following.

```

root@dragon:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdh[7](F) sdg[8](F) sdb[0] sdf[4] sde[3] sdd[2] sdc[1]
  3907049984 blocks super 0.91 level 5, 64k chunk, algorithm 2 [7/5] [UUUUU__]
    
unused devices: <none>

```

```

root@dragon:~# mdadm --detail /dev/md0
/dev/md0:
  Version : 00.91.03
  Creation Time : Fri Dec 5 17:39:06 2008
  Raid Level : raid5
   Array Size : 3907049984 (3726.05 GiB 4000.82 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
  Raid Devices : 7
  Total Devices : 7
Preferred Minor : 0
  Persistence : Superblock is persistent

  Update Time : Wed Jul 15 13:34:53 2009
  State : clean, degraded
 Active Devices : 5
Working Devices : 5
 Failed Devices : 2
  Spare Devices : 0

  Layout : left-symmetric
  Chunk Size : 64K

  Delta Devices : 2, (5->7)

  UUID : efc5da63:7c1465a1:b17889af:ac727b79 (local to host dragon)
  Events : 0.89336

  Number Major Minor RaidDevice State
  0 8 16 0 active sync /dev/sdb
   1 8 32 1 active sync /dev/sdc
  2 8 48 2 active sync /dev/sdd
  3 8 64 3 active sync /dev/sde
  4 8 80 4 active sync /dev/sdf
   7 8 112 5 faulty spare rebuilding /dev/sdh
  8 8 96 6 faulty spare rebuilding /dev/sdg

```


I am running Ubuntu 8.04 Server Edition.

 ```

root@dragon:~# uname -a
Linux dragon 2.6.24-19-server #1 SMP Wed Aug 20 18:43:06 UTC 2008 x86_64 GNU/Linux

```

I was upgrading from 5 1TB discs to 7 1TB discs in a raid 5

```

root@dragon:~# fdisk -l
 Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdf doesn't contain a valid partition table

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdg doesn't contain a valid partition table

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdh doesn't contain a valid partition table
 
```
I attempted to force the drive to be assembled in hopes that it would assemble and continue reshaping.
```

root@dragon:~# mdadm --assemble --force /dev/md0
 mdadm: device /dev/md0 already active - cannot assemble it

```
Originally, 5 discs were in the raid, bcdef. I was attempting to add gh. Being as two discs seemed to fail simultaneously, I feel like this may be an issue with the SATA card used to control those two discs. Alternately, it has been suggested to me that perhaps the power supply could not handle it as it is a generic 600 watt power supply running 9 hard drives. To replace the sata card as well as the replace the power supply, I would have to shut down the system which seems like I needed to have backed up the files in the beginning to allow the reshape to continue.

Additionally, here are what seems to be the what was dumped to syslog at about the time of the failure. At least, that's what it seems to me.

```

Jul 15 07:22:19 dragon kernel: [2793877.498293] res 51/04:00:00:ff:ff/00:00:00:00:00/ef Emask 0x1 (device error)
Jul 15 07:22:19 dragon kernel: [2793877.498519] res 51/04:00:00:ff:ff/00:00:00:00:00/ef Emask 0x1 (device error)
Jul 15 07:22:19 dragon kernel: [2793877.559267] ata8.00: configured for UDMA/133
Jul 15 07:22:19 dragon kernel: [2793877.559275] ata8: EH complete
Jul 15 07:22:19 dragon kernel: [2793877.559370] ata7.00: configured for UDMA/133
Jul 15 07:22:19 dragon kernel: [2793877.559374] ata7: EH complete
Jul 15 07:22:19 dragon kernel: [2793877.559712] res 51/04:00:00:ff:ff/00:00:00:00:00/ef Emask 0x1 (device error)
Jul 15 07:22:19 dragon kernel: [2793877.559940] res 51/04:00:00:ff:ff/00:00:00:00:00/ef Emask 0x1 (device error)
Jul 15 07:22:19 dragon kernel: [2793877.619134] ata7.00: configured for UDMA/133
Jul 15 07:22:19 dragon kernel: [2793877.619140] ata7: EH complete
Jul 15 07:22:19 dragon kernel: [2793877.619230] ata8.00: configured for UDMA/133
Jul 15 07:22:19 dragon kernel: [2793877.619233] ata8: EH complete
Jul 15 07:22:19 dragon kernel: [2793877.619596] res 51/04:00:00:ff:ff/00:00:00:00:00/ef Emask 0x1 (device error)
Jul 15 07:22:19 dragon kernel: [2793877.619878] res 51/04:00:00:ff:ff/00:00:00:00:00/ef Emask 0x1 (device error)
Jul 15 07:22:19 dragon kernel: [2793877.679012] ata7.00: configured for UDMA/133
Jul 15 07:22:19 dragon kernel: [2793877.679017] ata7: EH complete
Jul 15 07:22:19 dragon kernel: [2793877.679107] ata8.00: configured for UDMA/133
Jul 15 07:22:19 dragon kernel: [2793877.679110] ata8: EH complete
Jul 15 07:22:19 dragon kernel: [2793877.679453] res 51/04:00:00:ff:ff/00:00:00:00:00/ef Emask 0x1 (device error)
Jul 15 07:22:19 dragon kernel: [2793877.679734] res 51/04:00:00:ff:ff/00:00:00:00:00/ef Emask 0x1 (device error)
Jul 15 07:22:19 dragon kernel: [2793877.738876] ata8.00: configured for UDMA/133
Jul 15 07:22:19 dragon kernel: [2793877.738881] ata8: EH complete
Jul 15 07:22:19 dragon kernel: [2793877.738972] ata7.00: configured for UDMA/133
Jul 15 07:22:19 dragon kernel: [2793877.738975] ata7: EH complete
Jul 15 07:22:19 dragon kernel: [2793877.739318] res 51/04:00:00:ff:ff/00:00:00:00:00/ef Emask 0x1 (device error)
Jul 15 07:22:19 dragon kernel: [2793877.739600] res 51/04:00:00:ff:ff/00:00:00:00:00/ef Emask 0x1 (device error)
Jul 15 07:22:20 dragon kernel: [2793877.799993] ata7.00: configured for UDMA/133
Jul 15 07:22:20 dragon kernel: [2793877.799999] ata7: EH complete
Jul 15 07:22:20 dragon kernel: [2793877.800088] ata8.00: configured for UDMA/133
Jul 15 07:22:20 dragon kernel: [2793877.800091] ata8: EH complete
Jul 15 07:22:20 dragon kernel: [2793877.800450] res 51/04:00:00:ff:ff/00:00:00:00:00/ef Emask 0x1 (device error)
Jul 15 07:22:20 dragon kernel: [2793877.800726] res 51/04:00:00:ff:ff/00:00:00:00:00/ef Emask 0x1 (device error)
Jul 15 07:22:20 dragon kernel: [2793877.858626] ata7.00: configured for UDMA/133
Jul 15 07:22:20 dragon kernel: [2793877.858638] sd 6:0:0:0: [sdg] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 15 07:22:20 dragon kernel: [2793877.858643] sd 6:0:0:0: [sdg] Sense Key : Aborted Command [current] [descriptor]
Jul 15 07:22:20 dragon kernel: [2793877.858662] Descriptor sense data with sense descriptors (in hex):
Jul 15 07:22:20 dragon kernel: [2793877.858665] 72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00:
Jul 15 07:22:20 dragon kernel: [2793877.858674] 0f ff ff 00
Jul 15 07:22:20 dragon kernel: [2793877.858678] sd 6:0:0:0: [sdg] Add. Sense: No additional sense information
Jul 15 07:22:20 dragon kernel: [2793877.858683] end_request: I/O error, dev sdg, sector 268435200
Jul 15 07:22:20 dragon kernel: [2793877.858746] ata7: EH complete
Jul 15 07:22:20 dragon kernel: [2793877.858765] ata8.00: configured for UDMA/133
Jul 15 07:22:20 dragon kernel: [2793877.858773] sd 8:0:0:0: [sdh] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 15 07:22:20 dragon kernel: [2793877.858777] sd 8:0:0:0: [sdh] Sense Key : Aborted Command [current] [descriptor]
Jul 15 07:22:20 dragon kernel: [2793877.858781] Descriptor sense data with sense descriptors (in hex):
Jul 15 07:22:20 dragon kernel: [2793877.858783] 72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00
Jul 15 07:22:20 dragon kernel: [2793877.858793] 0f ff ff 00
Jul 15 07:22:20 dragon kernel: [2793877.858797] sd 8:0:0:0: [sdh] Add. Sense: No additional sense information
Jul 15 07:22:20 dragon kernel: [2793877.858800] end_request: I/O error, dev sdh, sector 268435200
Jul 15 07:22:20 dragon kernel: [2793877.858857] ata8: EH complete
Jul 15 07:22:20 dragon kernel: [2793878.190999] sd 6:0:0:0: [sdg] 1953525168 512-byte hardware sectors (1000205 MB)
Jul 15 07:22:20 dragon kernel: [2793878.191013] sd 6:0:0:0: [sdg] Write Protect is off
Jul 15 07:22:20 dragon kernel: [2793878.191030] sd 6:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 15 07:22:20 dragon kernel: [2793878.191051] sd 8:0:0:0: [sdh] 1953525168 512-byte hardware sectors (1000205 MB)
Jul 15 07:22:20 dragon kernel: [2793878.191059] sd 8:0:0:0: [sdh] Write Protect is off
Jul 15 07:22:20 dragon kernel: [2793878.191074] sd 8:0:0:0: [sdh] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 15 07:22:20 dragon kernel: [2793878.191088] sd 6:0:0:0: [sdg] 1953525168 512-byte hardware sectors (1000205 MB)
Jul 15 07:22:20 dragon kernel: [2793878.191096] sd 6:0:0:0: [sdg] Write Protect is off
Jul 15 07:22:20 dragon kernel: [2793878.191110] sd 6:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 15 07:22:20 dragon kernel: [2793878.318475] md: md0: reshape done.

```

So, unfortunately, as someone that probably has less experience than I should for doing this type of process, I am partially at a loss as to what to do. My ideas were the following

1. remove and hot add the drives back and try to get it to finish reshaping
2. take the original 5 drives, force them into a raid 5 of the same original type, salvage whatever I can from them, and format all the drives and start over.
3. do something involving swapping out the sata card for another one that hopefully works better

Any advice on what I should do instead? Sorry for the long long post, I wanted to have as much information ready as possible. I would really appreciate the help.

---

### Post by fjgaude on 2009-07-17
Well, it's hard to say just what is the issue here.

I'd do your 1., fault each of the two drives, remove them, using **mdadm**, and then I'd zero their superblocks. Then I'd test them to see if they are good drives in that particular controller you have. If they are I'd add them back and see what happens.

I suppose we are dealing with media files on such a large array? You have no easy backups?

---

### Post by Xaga on 2009-07-17
I've got it rebuilding again, thanks to mdadm 2.6.4. This thread really is wonderful:

[http://ubuntuforums.org/showthread.php?t=833191](http://ubuntuforums.org/showthread.php?t=833191)

---

