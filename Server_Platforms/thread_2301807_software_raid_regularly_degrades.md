---
title: "software raid regularly degrades"
date: 2015-11-05
forum: Server Platforms
---

### Post by viktor18 on 2015-11-05
Hi, 
I have a software raid setup on md1 that every 2 days will reliably degrade with one of the two drives (random) "failing". I then re-add that drive, it resyncs for a few hours and then everything is fine for the next two days. syslog indicates something is wrong with swiotlb at the time the drive degrades. I don't actually think swiotlb errors are problematic as they continue even after the drive raid array degrades. I tried increasing swiotlb buffer size from 64 to 128MB which seems to increase the time till failure a little bit (extra day or so, not much).


```
Oct 28 21:00:55 frycedes kernel: [162876.240429] ata_piix 0000:00:1f.5: swiotlb buffer is fullOct 28 21:00:55 frycedes kernel: [162876.240431] DMA: Out of SW-IOMMU space for 65536 bytes at device 0000:00:1f.5
Oct 28 21:00:55 frycedes kernel: [162876.240449] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct 28 21:00:55 frycedes kernel: [162876.240452] ata3.00: failed command: WRITE DMA EXT
Oct 28 21:00:55 frycedes kernel: [162876.240457] ata3.00: cmd 35/00:00:00:74:18/00:04:14:00:00/e0 tag 0 dma 524288 out
Oct 28 21:00:55 frycedes kernel: [162876.240457]          res 50/00:00:af:88:e0/00:00:e8:00:00/e0 Emask 0x40 (internal error)
Oct 28 21:00:55 frycedes kernel: [162876.240459] ata3.00: status: { DRDY }
Oct 28 21:00:55 frycedes kernel: [162876.241068] ata2.00: configured for UDMA/133
Oct 28 21:00:55 frycedes kernel: [162876.256298] ata3.00: configured for UDMA/133
Oct 28 21:00:55 frycedes kernel: [162876.256303] ata3: EH complete
Oct 28 21:00:55 frycedes kernel: [162876.256475] ata_piix 0000:00:1f.5: swiotlb buffer is full
Oct 28 21:00:55 frycedes kernel: [162876.256478] DMA: Out of SW-IOMMU space for 65536 bytes at device 0000:00:1f.5
Oct 28 21:00:55 frycedes kernel: [162876.256497] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct 28 21:00:55 frycedes kernel: [162876.256500] ata3.00: failed command: WRITE DMA EXT
Oct 28 21:00:55 frycedes kernel: [162876.256505] ata3.00: cmd 35/00:00:00:74:18/00:04:14:00:00/e0 tag 0 dma 524288 out
Oct 28 21:00:55 frycedes kernel: [162876.256505]          res 50/00:00:af:88:e0/00:00:e8:00:00/e0 Emask 0x40 (internal error)
Oct 28 21:00:55 frycedes kernel: [162876.256507] ata3.00: status: { DRDY }
Oct 28 21:00:55 frycedes kernel: [162876.256585] ata2.01: configured for UDMA/133
Oct 28 21:00:55 frycedes kernel: [162876.256591] ata2: EH complete
Oct 28 21:00:55 frycedes kernel: [162876.256683] ata_piix 0000:00:1f.2: swiotlb buffer is full
Oct 28 21:00:55 frycedes kernel: [162876.256685] DMA: Out of SW-IOMMU space for 65536 bytes at device 0000:00:1f.2
Oct 28 21:00:55 frycedes kernel: [162876.256706] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct 28 21:00:55 frycedes kernel: [162876.256709] ata2.00: failed command: WRITE DMA EXT
Oct 28 21:00:55 frycedes kernel: [162876.256714] ata2.00: cmd 35/00:50:00:a4:86/00:01:88:00:00/e0 tag 0 dma 172032 out
Oct 28 21:00:55 frycedes kernel: [162876.256714]          res 50/00:00:af:6d:70/00:00:74:00:00/f0 Emask 0x40 (internal error)
Oct 28 21:00:55 frycedes kernel: [162876.256716] ata2.00: status: { DRDY }
Oct 28 21:00:55 frycedes kernel: [162876.273090] ata2.00: configured for UDMA/133
Oct 28 21:00:55 frycedes kernel: [162876.273261] ata3.00: configured for UDMA/133
Oct 28 21:00:55 frycedes kernel: [162876.273266] ata3: EH complete
Oct 28 21:00:55 frycedes kernel: [162876.273453] ata_piix 0000:00:1f.5: swiotlb buffer is full
Oct 28 21:00:55 frycedes kernel: [162876.273455] DMA: Out of SW-IOMMU space for 65536 bytes at device 0000:00:1f.5
Oct 28 21:00:55 frycedes kernel: [162876.273475] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct 28 21:00:55 frycedes kernel: [162876.273478] ata3.00: failed command: WRITE DMA EXT
Oct 28 21:00:55 frycedes kernel: [162876.273482] ata3.00: cmd 35/00:00:00:74:18/00:04:14:00:00/e0 tag 0 dma 524288 out
Oct 28 21:00:55 frycedes kernel: [162876.273482]          res 50/00:00:af:88:e0/00:00:e8:00:00/e0 Emask 0x40 (internal error)
Oct 28 21:00:55 frycedes kernel: [162876.273485] ata3.00: status: { DRDY }
Oct 28 21:00:55 frycedes kernel: [162876.288308] ata3.00: configured for UDMA/133
Oct 28 21:00:55 frycedes kernel: [162876.288318] sd 2:0:0:0: [sdd]  
Oct 28 21:00:55 frycedes kernel: [162876.288320] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 28 21:00:55 frycedes kernel: [162876.288322] sd 2:0:0:0: [sdd]  
Oct 28 21:00:55 frycedes kernel: [162876.288324] Sense Key : Aborted Command [current] [descriptor]
Oct 28 21:00:55 frycedes kernel: [162876.288327] Descriptor sense data with sense descriptors (in hex):
Oct 28 21:00:55 frycedes kernel: [162876.288328]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Oct 28 21:00:55 frycedes kernel: [162876.288335]         e8 e0 88 af 
Oct 28 21:00:55 frycedes kernel: [162876.288339] sd 2:0:0:0: [sdd]  
Oct 28 21:00:55 frycedes kernel: [162876.288341] Add. Sense: No additional sense information
Oct 28 21:00:55 frycedes kernel: [162876.288343] sd 2:0:0:0: [sdd] CDB: 
Oct 28 21:00:55 frycedes kernel: [162876.288344] Write(10): 2a 00 14 18 74 00 00 04 00 00
Oct 28 21:00:55 frycedes kernel: [162876.288351] end_request: I/O error, dev sdd, sector 337146880
Oct 28 21:00:55 frycedes kernel: [162876.288363] ata3: EH complete
Oct 28 21:00:55 frycedes kernel: [162876.288665] ata2.01: configured for UDMA/133
Oct 28 21:00:55 frycedes kernel: [162876.288673] sd 1:0:0:0: [sdb]  
Oct 28 21:00:55 frycedes kernel: [162876.288675] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 28 21:00:55 frycedes kernel: [162876.288677] sd 1:0:0:0: [sdb]  
Oct 28 21:00:55 frycedes kernel: [162876.288678] Sense Key : Aborted Command [current] [descriptor]
Oct 28 21:00:55 frycedes kernel: [162876.288681] Descriptor sense data with sense descriptors (in hex):
Oct 28 21:00:55 frycedes kernel: [162876.288683]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Oct 28 21:00:55 frycedes kernel: [162876.288690]         74 70 6d af 
Oct 28 21:00:55 frycedes kernel: [162876.288694] sd 1:0:0:0: [sdb]  
Oct 28 21:00:55 frycedes kernel: [162876.288695] Add. Sense: No additional sense information
Oct 28 21:00:55 frycedes kernel: [162876.288698] sd 1:0:0:0: [sdb] CDB: 
Oct 28 21:00:55 frycedes kernel: [162876.288699] Write(10): 2a 00 88 86 a4 00 00 01 50 00
Oct 28 21:00:55 frycedes kernel: [162876.288705] end_request: I/O error, dev sdb, sector 2290525184
Oct 28 21:00:55 frycedes kernel: [162876.288719] ata2: EH complete
Oct 28 21:00:55 frycedes kernel: [162876.288733] md/raid10:md1: Disk failure on sdd1, disabling device.
Oct 28 21:00:55 frycedes kernel: [162876.288733] md/raid10:md1: Operation continuing on 1 devices.
Oct 28 21:00:55 frycedes kernel: [162876.288744] EXT4-fs warning (device md1): ext4_end_bio:317: I/O error -5 writing to inode 39289321 (offset 0 size 0 starting block 84220288)

```


```
% sudo mdadm --examine --scan 
ARRAY /dev/md/1 metadata=1.2 UUID=df392ede:2469dc38:2a80c611:c66357f3 name=frycedes:1

```

```
% sudo mdadm -D /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Sat Oct 10 21:28:30 2015
     Raid Level : raid10
     Array Size : 1953380352 (1862.89 GiB 2000.26 GB)
  Used Dev Size : 1953380352 (1862.89 GiB 2000.26 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Thu Nov  5 10:58:07 2015
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0


         Layout : far=2
     Chunk Size : 512K


           Name : frycedes:1  (local to host frycedes)
           UUID : df392ede:2469dc38:2a80c611:c66357f3
         Events : 191477


    Number   Major   Minor   RaidDevice State
       3       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed


       2       8       49        -      faulty spare   /dev/sdd1



```

---

### Post by SeijiSensei on 2015-11-05
The drive has a hardware problem. You can only solve it by replacing the device itself.

---

### Post by viktor18 on 2015-11-05
It's not always the same drive, sometimes sdd1 and sometimes sdb1. sdd1 is brand new.

---

