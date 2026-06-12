---
title: "HELP! LXLE damaged my XP partition, but then ..."
date: 2016-08-15
forum: Ubuntu/Debian BASED
---

### Post by new-fish on 2016-08-15
after too many fumbling attempts to repair, Gparted reports my entire disk is now unallocated (! Warning: /dev/sda: unrecognized disk label). I didn't freak out too badly, as I was sure not enough time was spent to wipe my disk. HA HA. Anyway, along the way I logged a number of  Boot Info Script reports to pastebin and I'm hoping to get advice on the best course to recover my partitions.


My last report is at [http://paste2.org/p7hJhX8z](http://paste2.org/p7hJhX8z). It shows:
```
 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]




============================= Boot Info Summary: ===============================


 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''


sda2: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''


sda6: __________________________________________________________________________


    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''


sda7: __________________________________________________________________________


    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''


sda4: __________________________________________________________________________


    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
[/QUOTE]
and
[QUOTE]======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sda1




Unknown BootLoader on sda2


00000000  84 30 88 30 98 30 9c 30  ac 30 b0 30 c0 30 c4 30  |.0.0.0.0.0.0.0.0|
00000010  d4 30 d8 30 e8 30 ec 30  fc 30 00 31 10 31 14 31  |.0.0.0.0.0.1.1.1|
00000020  24 31 28 31 38 31 3c 31  4c 31 50 31 60 31 64 31  |$1(181<1L1P1`1d1|
00000030  68 31 80 31 84 31 88 31  9c 31 ac 31 b0 31 b4 31  |h1.1.1.1.1.1.1.1|
00000040  cc 31 d0 31 d4 31 e8 31  f8 31 fc 31 00 32 18 32  |.1.1.1.1.1.1.2.2|
00000050  1c 32 20 32 34 32 44 32  48 32 4c 32 64 32 68 32  |.2 242D2H2L2d2h2|
00000060  6c 32 80 32 90 32 94 32  98 32 b0 32 b4 32 c8 32  |l2.2.2.2.2.2.2.2|
00000070  d8 32 dc 32 e0 32 f8 32  fc 32 10 33 20 33 24 33  |.2.2.2.2.2.3 3$3|
00000080  28 33 40 33 44 33 48 33  4c 33 50 33 54 33 68 33  |([email protected]|
00000090  78 33 7c 33 8c 33 90 33  94 33 ac 33 b0 33 b4 33  |x3|3.3.3.3.3.3.3|
000000a0  b8 33 bc 33 d0 33 d4 33  ec 33 f0 33 f4 33 f8 33  |.3.3.3.3.3.3.3.3|
000000b0  fc 33 00 34 14 34 24 34  28 34 38 34 3c 34 40 34  |.3.4.4$4(484<[email protected]|
000000c0  58 34 5c 34 74 34 78 34  90 34 94 34 98 34 ac 34  |X4\4t4x4.4.4.4.4|
000000d0  b0 34 c8 34 cc 34 e4 34  e8 34 ec 34 f0 34 04 35  |.4.4.4.4.4.4.4.5|
000000e0  14 35 18 35 1c 35 34 35  38 35 4c 35 5c 35 60 35  |.5.5.54585L5\5`5|
000000f0  70 35 74 35 84 35 88 35  8c 35 a4 35 a8 35 c0 35  |p5t5.5.5.5.5.5.5|
00000100  c4 35 c8 35 cc 35 d0 35  d4 35 d8 35 dc 35 e0 35  |.5.5.5.5.5.5.5.5|
00000110  e4 35 f8 35 08 36 0c 36  1c 36 20 36 24 36 3c 36  |.5.5.6.6.6 6$6<6|
00000120  40 36 58 36 5c 36 60 36  64 36 68 36 6c 36 70 36  |@6X6\6`6d6h6l6p6|
00000130  74 36 88 36 98 36 9c 36  a0 36 b8 36 bc 36 d0 36  |t6.6.6.6.6.6.6.6|
00000140  e0 36 e4 36 e8 36 00 37  04 37 18 37 28 37 2c 37  |.6.6.6.7.7.7(7,7|
00000150  30 37 48 37 4c 37 50 37  54 37 58 37 5c 37 70 37  |07H7L7P7T7X7\7p7|
00000160  80 37 84 37 88 37 a0 37  a4 37 a8 37 ac 37 b0 37  |.7.7.7.7.7.7.7.7|
00000170  c4 37 d4 37 d8 37 dc 37  f4 37 f8 37 fc 37 00 38  |.7.7.7.7.7.7.7.8|
00000180  14 38 24 38 28 38 2c 38  44 38 48 38 4c 38 50 38  |.8$8(8,8D8H8L8P8|
00000190  64 38 74 38 78 38 7c 38  94 38 98 38 9c 38 b0 38  |d8t8x8|8.8.8.8.8|
000001a0  b4 38 cc 38 d0 38 d4 38  d8 38 ec 38 fc 38 00 39  |.8.8.8.8.8.8.8.9|
000001b0  04 39 1c 39 20 39 24 39  38 39 48 39 4c 39 50 39  |.9.9 9$989H9L9P9|
000001c0  54 39 58 39 5c 39 60 39  64 39 68 39 6c 39 70 39  |T9X9\9`9d9h9l9p9|
000001d0  74 39 78 39 7c 39 80 39  84 39 88 39 8c 39 90 39  |t9x9|9.9.9.9.9.9|
000001e0  94 39 98 39 a0 39 a4 39  a8 39 ac 39 b0 39 b4 39  |.9.9.9.9.9.9.9.9|
000001f0  b8 39 bc 39 c0 39 c4 39  cc 39 d0 39 d4 39 d8 39  |.9.9.9.9.9.9.9.9|
00000200


Unknown BootLoader on sda5




Unknown BootLoader on sda6




Unknown BootLoader on sda7




Unknown BootLoader on sda4






=============================== StdErr Messages: ===============================


hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
File descriptor 8 (/proc/11553/mounts) leaked on lvs invocation. Parent PID 17020: bash
File descriptor 63 (pipe:[59906]) leaked on lvs invocation. Parent PID 17020: bash

```


HALP!

---

### Post by wildmanne39 on 2016-08-15
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by arochester on 2016-08-15
LXLE an Ubuntu derivative. Move to [https://ubuntuforums.org/forumdisplay.php?f=452](https://ubuntuforums.org/forumdisplay.php?f=452) ?

LXLE has its own Forums [http://lxle.net/forums/](http://lxle.net/forums/)

---

### Post by oldfred on 2016-08-15
Disk label is whether it is dos, gpt or one of many others.
Your report shows it as dos which would be correct for an old XP drive.

The partition table shows no errors. But a bit strange that sda4 is at beginning of drive and sda1 is at end.
And partitions are not at normal start locations. With old XP installs first partition on drive would start at sector 63.

Then if partition structure is not correct, it will not see format & files in partition as they then are not at correct place.
Do you have a copy of original drive structure somewhere?

---

### Post by howefield on 2016-08-15
Moved to the "*Ubuntu/Debian BASED*" forum.,

---

### Post by new-fish on 2016-08-15
Thanks for the responses. Using testdisk, I changed the first (XP) partition to boot-able, marked the partitions primary/logical as appropriate, wrote the partition table, and rebuilt the XP partition's boot sector (which only changed two bytes). Gparted now sees the partitions. I then ran boot-repair and am almost back to the point just before the drive was "deallocated". My Ubuntu MATE partition was not discovered by boot-repair and XP still won't boot after selection in Grub menu.

What is the best way to diagnose the MATE partition? What tricks for the XP partition? Now searching ...

---

### Post by oldfred on 2016-08-15
If partition is correct, you may need to run chkdsk from Windows repair console on NTFS or FAT partiitons. Or run fsck on ext4 partitions to repair corruption. But if partition is mis-aligned that may not work.

---

### Post by LostFarmer on 2016-08-16
create a new Boot Info Script report for us to see just what changes were made.

Can you mount the Xp partition with linux ?

---

### Post by new-fish on 2016-08-19
Thanks again, all. I tried two methods of repairing the partition in XP's Recovery Console, one of which ran chkdsk with a clean bill of health. LXLE mounted and could read the partition. However, no boot. I finally concluded that I had damaged the partition by squeezing it with gparted. Fortunately, Windows Update still works and I was able to reinstall the minimal system I had there. Still some cleanup but everything seems ok.

Thanks again.

---

