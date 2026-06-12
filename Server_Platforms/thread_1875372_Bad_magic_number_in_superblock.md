---
title: "Bad magic number in superblock"
date: 2011-11-04
forum: Server Platforms
---

### Post by shredIt on 2011-11-04
Hi folks,

I've got a private ftp server in my room and i was doing some data transfer when the electricity in my flat crashed.

Now I've got the following problem.

One of my disk drives shows me at boot up the following:

```
955.065129] Buffer I/O error on device sdc, logical block 8
[  957.530110] sd 7:0:0:0: [sdc] Unhandled sense code
[  957.530118] sd 7:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  957.530125] sd 7:0:0:0: [sdc]  Sense Key : Medium Error [current] 
[  957.530134] sd 7:0:0:0: [sdc]  Add. Sense: Unrecovered read error
[  957.530143] sd 7:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 40 00 00 08 00
[  957.530160] end_request: I/O error, dev sdc, sector 64
[  957.530166] Buffer I/O error on device sdc, logical block 8
[ 1041.980988] sd 7:0:0:0: [sdc] Unhandled sense code
[ 1041.980992] sd 7:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1041.980996] sd 7:0:0:0: [sdc]  Sense Key : Medium Error [current] 
[ 1041.980999] sd 7:0:0:0: [sdc]  Add. Sense: Unrecovered read error
[ 1041.981003] sd 7:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 20 00 00 40 00
[ 1041.981010] end_request: I/O error, dev sdc, sector 32
[ 1041.981013] Buffer I/O error on device sdc, logical block 4
[ 1041.981018] Buffer I/O error on device sdc, logical block 5
[ 1041.981020] Buffer I/O error on device sdc, logical block 6
[ 1041.981022] Buffer I/O error on device sdc, logical block 7
[ 1041.981024] Buffer I/O error on device sdc, logical block 8
[ 1041.981026] Buffer I/O error on device sdc, logical block 9
[ 1041.981028] Buffer I/O error on device sdc, logical block 10
[ 1041.981030] Buffer I/O error on device sdc, logical block 11

```

The above is a short preview. The list runs and runs through..... the whole time....
but only the drive sdc is affected!!

My sdc drive hast the following parameters:
```

Drive /dev/sdc: 2000.4 GByte, 2000398934016 Byte
255 Heads, 63 Sectors/Track, 243201 Cyclinder
Units = Cyclinder from 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00072fd5

```


If I run fsck -v /dev/sdc the following is returned:
Superblock is unreadable or describes a non valid ext2 file system
Bad magic number in superblock while trying to open dev/sdc...

I tried e2fsck and tune2fs with various parameters but had no luck...

Does anyone has any idea on how to reset the value of the superblock??

I can't reset the whole file system...!!!

---

### Post by rubylaser on 2011-11-04
Have you tried using an [alternate superblock]("http://www.cyberciti.biz/faq/linux-find-alternative-superblocks/")?

---

