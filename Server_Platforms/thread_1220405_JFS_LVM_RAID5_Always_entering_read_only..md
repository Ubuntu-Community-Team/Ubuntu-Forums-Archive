---
title: "JFS LVM RAID5 Always entering read only."
date: 2009-07-22
forum: Server Platforms
---

### Post by kripz on 2009-07-22
I'm sick of it. Wasted 8 hours testing my RAM and 4 Samsung drives with Samsung diagnostics tool and smartmon tools... which all passed of course.

It all happened after i expanded the array from 3 to 4 drives. I added the device to the array and it rebuilt. I then grew the LVM and then did a mount -o remount,resize -t jfs /dev/lvm-raid5/lvm0 /storage/

Its pretty random, i might copy several 100's of GB of data or maybe a touch will lock it.

Heres the latest error

> :~# dmesg
... TRIMMED
[107884.263490] ERROR: (device dm-0): diAllocIno: nfreeinos = 0, but iag on freelist
 
 
:~# fsck.jfs /dev/lvm-raid5/lvm0 -v
fsck.jfs version 1.1.12, 24-Aug-2007
processing started: 7/22/2009 21.34.29
Using default parameter: -p
The current device is:  /dev/lvm-raid5/lvm0
Open(...READ/WRITE EXCLUSIVE...) returned rc = 0
Primary superblock is valid.
The type of file system for the device is JFS.
Block size in bytes:  4096
Filesystem size in blocks:  732569600
**Phase 0 - Replay Journal Log
LOGREDO:  Allocating for ReDoPage:  (d) 4096 bytes
LOGREDO:  Allocating for NoDoFile:  (d) 4096 bytes
LOGREDO:  Allocating for BMap:  (d) 1456800 bytes
LOGREDO:  Allocating for IMap:  (d) 18272 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for DoBLk:  (d) 4096 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for DoBLk:  (d) 4096 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Allocating for IMap:  (d) 2048 bytes
LOGREDO:  Log record for Sync Point at:    0x068d3a4
LOGREDO:  Allocating for DoBLk:  (d) 4096 bytes
LOGREDO:  Beginning to update the Inode Allocation Map.
LOGREDO:  Done updating the Inode Allocation Map.
LOGREDO:  Beginning to update the Block Map.
LOGREDO:  Done updating the Block Map.
LOGREDO:  End of log found at logend = 0x06cb898
LOGREDO:  Synch point record number:  0x068d3a4
LOGREDO:  Synch point record address:  0x0657470
LOGREDO:  Number of log records:    (d) 4640
LOGREDO:  Number of Do blocks:    (d) 240
LOGREDO:  Number of NoDo blocks:    (d) 0
logredo returned rc = 0
**Phase 1 - Check Blocks, Files/Directories, and  Directory Entries
**Phase 2 - Count links
**Phase 3 - Duplicate Block Rescan and Directory Connectedness
**Phase 4 - Report Problems
**Phase 5 - Check Connectivity
**Phase 6 - Perform Approved Corrections
**Phase 7 - Rebuild File/Directory Allocation Maps
**Phase 8 - Rebuild Disk Allocation Maps
Filesystem Summary:
Blocks in use for inodes:  3772
Inode count:  30176
File count:  22721
Directory count:  635
Block count:  732569600
Free block count:  348742811
2930278400 kilobytes total disk space.
     4593 kilobytes in 635 directories.
1534818068 kilobytes in 22721 user files.
       80 kilobytes in extended attributes
        0 kilobytes in access control lists
   493601 kilobytes reserved for system use.
1394971244 kilobytes are available for use.
Filesystem is clean.
All observed inconsistencies have been repaired.
Filesystem has been marked clean.
**** Filesystem was modified. ****
processing terminated:  7/22/2009 21:35:16  with return code: 0  exit code: 0.

A previous error a couple of days ago.

> [17589.811677] ERROR: (device dm-0): diFree: numfree > numinos
[17589.881241] ERROR: (device dm-0): diFree: numfree > numinos
[17589.881241] ERROR: (device dm-0): diFree: numfree > numinos
[17589.881241] ERROR: (device dm-0): diFree: numfree > numinos
[17589.881241] ERROR: (device dm-0): diFree: numfree > numinos
[17589.882617] ERROR: (device dm-0): diFree: numfree > numinos
[17589.882673] ERROR: (device dm-0): diFree: numfree > numinos
[17589.882617] ERROR: (device dm-0): diFree: numfree > numinos
[17589.882674] ERROR: (device dm-0): diFree: numfree > numinos
[17589.882674] ERROR: (device dm-0): diFree: numfree > numinos
[17589.882674] ERROR: (device dm-0): diFree: numfree > numinos
[17589.882674] ERROR: (device dm-0): diFree: numfree > numinos
[17589.894096] ERROR: (device dm-0): diFree: numfree > numinos
[17589.894096] ERROR: (device dm-0): diFree: numfree > numinos
[17589.894096] ERROR: (device dm-0): diFree: numfree > numinos
[17589.894096] ERROR: (device dm-0): diFree: numfree > numinos
[17589.896338] ERROR: (device dm-0): diFree: numfree > numinos
[17589.896338] ERROR: (device dm-0): diFree: numfree > numinos
[17589.896353] ERROR: (device dm-0): diFree: numfree > numinos
[17596.961946] ERROR: (device dm-0): diFree: numfree > numinos
[17596.961946] ERROR: (device dm-0): diFree: numfree > numinos
[17596.962413] ERROR: (device dm-0): diFree: numfree > numinos

Kernel: 2.6.26-1-686

---

