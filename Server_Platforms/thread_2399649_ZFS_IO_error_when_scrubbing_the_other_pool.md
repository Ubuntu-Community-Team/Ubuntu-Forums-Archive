---
title: "ZFS I/O error when scrubbing the other pool"
date: 2018-08-28
forum: Server Platforms
---

### Post by thegarbz@yahoo.com.au on 2018-08-28
Hey guys I have a bit of a perplexing one here. Currently I have 2 zpools, pool1 and pool2. Since creating pool1 2 weeks ago I get approximately 6 I/O errors randomly across disks on pool1, ... but only when scrubbing pool2. No problems occur during this other than an error message in dmesg. No devices drop offline and the system is unaffected. 

**Quick history:**
pool1 and pool2 are both the same size, 12TB.
pool2 which is functioning normally was grown from a smaller pool during my last HDD failure by replacing drives one at a time.
pool1 was destined to have the same happen 3 weeks ago but due to an incorrect ashift value I sent the old pool1 to a file, rebuilt pool1 from scratch and then imported it again. Since then I have experienced this problem. 

Things I have checked:
- Cables
- Firmware of HDDs (all 6 WD Reds in my NAS now have identical firmware)
- zpool created in identical was between poo1 and pool2.
- used hdparm to prevent idle spindown of the drives in pool1.
- pool1 passes scrub without issue. No performance issues at all reading or writing to the pool. No smart errors.

I'm normally pretty good at figuring things out but I don't really know where to look next for this. Has anyone seen something like this or have any suggestions what to do next?

zpool events: pool1 scrubs monday, pool2 scrubs tuesday. All io and delay errors are pool1. (pool2 scrub still in progress)
```
Aug 20 2018 02:10:02.017707822 ereport.fs.zfs.scrub.startAug 20 2018 03:57:03.840961405 ereport.fs.zfs.scrub.finish
Aug 21 2018 02:10:01.954106448 ereport.fs.zfs.scrub.start
Aug 21 2018 02:45:57.216337412 ereport.fs.zfs.delay
Aug 21 2018 02:45:57.216337412 ereport.fs.zfs.io
Aug 21 2018 06:27:26.238039391 ereport.fs.zfs.delay
Aug 21 2018 06:27:26.238039391 ereport.fs.zfs.io
Aug 21 2018 07:50:27.236790933 ereport.fs.zfs.delay
Aug 21 2018 07:50:27.236790933 ereport.fs.zfs.io
Aug 21 2018 08:20:53.233356411 ereport.fs.zfs.delay
Aug 21 2018 08:20:53.233356411 ereport.fs.zfs.io
Aug 21 2018 10:07:19.274951900 ereport.fs.zfs.delay
Aug 21 2018 10:07:19.274951900 ereport.fs.zfs.io
Aug 21 2018 11:32:58.286729955 ereport.fs.zfs.delay
Aug 21 2018 11:32:58.286729955 ereport.fs.zfs.io
Aug 21 2018 16:35:31.819410659 ereport.fs.zfs.scrub.finish
Aug 27 2018 02:10:01.898095120 ereport.fs.zfs.scrub.start
Aug 27 2018 04:00:07.826703267 ereport.fs.zfs.scrub.finish
Aug 28 2018 02:10:02.127339048 ereport.fs.zfs.scrub.start
Aug 28 2018 02:11:17.278888008 ereport.fs.zfs.delay
Aug 28 2018 02:11:17.278888008 ereport.fs.zfs.io
Aug 28 2018 05:28:24.308869698 ereport.fs.zfs.delay
Aug 28 2018 05:28:24.308869698 ereport.fs.zfs.io
Aug 28 2018 06:27:45.246703350 ereport.fs.zfs.delay
Aug 28 2018 06:27:45.246703350 ereport.fs.zfs.io
Aug 28 2018 07:32:41.339504651 ereport.fs.zfs.delay
Aug 28 2018 07:32:41.339504651 ereport.fs.zfs.io
Aug 28 2018 08:30:02.412413627 ereport.fs.zfs.delay
Aug 28 2018 08:30:02.412413627 ereport.fs.zfs.io
```

An example dmesg of the associated errors:
```
[746024.042415] ata10.00: exception Emask 0x0 SAct 0x4000 SErr 0x0 action 0x6 frozen
[746024.042430] ata10.00: failed command: WRITE FPDMA QUEUED
[746024.042447] ata10.00: cmd 61/08:70:a8:77:c0/00:00:d1:01:00/40 tag 14 ncq 4096 out
                         res 40/00:ff:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[746024.042455] ata10.00: status: { DRDY }
[746024.042466] ata10: hard resetting link
[746024.374382] ata10: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[746024.376071] ata10.00: configured for UDMA/133
[746024.376091] sd 9:0:0:0: [sde] tag#14 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[746024.376097] sd 9:0:0:0: [sde] tag#14 Sense Key : Illegal Request [current] [descriptor]
[746024.376102] sd 9:0:0:0: [sde] tag#14 Add. Sense: Unaligned write command
[746024.376107] sd 9:0:0:0: [sde] tag#14 CDB: Write(16) 8a 00 00 00 00 01 d1 c0 77 a8 00 00 00 08 00 00
[746024.376113] blk_update_request: I/O error, dev sde, sector 7814018984
[746024.376139] ata10: EH complete
[749465.119407] ata12.00: exception Emask 0x0 SAct 0x10 SErr 0x0 action 0x6 frozen
[749465.119416] ata12.00: failed command: WRITE FPDMA QUEUED
[749465.119424] ata12.00: cmd 61/08:20:00:77:c0/00:00:d1:01:00/40 tag 4 ncq 4096 out
                         res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[749465.119428] ata12.00: status: { DRDY }
[749465.119434] ata12: hard resetting link
[749465.455434] ata12: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[749465.457286] ata12.00: configured for UDMA/133
[749465.457319] sd 11:0:0:0: [sdg] tag#4 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[749465.457331] sd 11:0:0:0: [sdg] tag#4 Sense Key : Illegal Request [current] [descriptor]
[749465.457340] sd 11:0:0:0: [sdg] tag#4 Add. Sense: Unaligned write command
[749465.457351] sd 11:0:0:0: [sdg] tag#4 CDB: Write(16) 8a 00 00 00 00 01 d1 c0 77 00 00 00 00 08 00 00
[749465.457358] blk_update_request: I/O error, dev sdg, sector 7814018816
[749465.457406] ata12: EH complete
```

---

