---
title: "mdadm raid1 doesn't finish syncing"
date: 2010-11-14
forum: Server Platforms
---

### Post by moparisthebest on 2010-11-14
One of the hard drives in my server failed the other day, backups saved the day and downtime was only a few hours, but when setting up the new drive I went ahead and migrated to software RAID, in the hopes it may give me less downtime in the future when a drive fails.  It all went rather well, but my main root partition won't finish syncing for some reason.

sda was the original drive with sda4 as /, sda1 as /boot, and sda2 as swap.  sdb was the drive that failed and was replaced with the new drive.  So I set up sdb with the same partitions of sda, added it to a RAID1 array, copied files from sda, and reboot to md4 as /, md1 as /boot, and md2 as swap.  I added the sda partitions to the array, and the sync went off without a hitch on md1 and md2, md4 progresses well, but after a few hours /proc/mdstat just shows this:

```
root@d668:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sdb2[1] sda2[0]
      9767424 blocks [2/2] [UU]
      
md1 : active raid1 sdb1[1] sda1[0]
      144448 blocks [2/2] [UU]
      
md4 : active raid1 sda4[2] sdb4[1]
      478471808 blocks [2/1] [_U]
      
unused devices: <none>
root@d668:~# mdadm --detail /dev/md4
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
/dev/md4:
        Version : 00.90
  Creation Time : Thu Nov 11 09:53:01 2010
     Raid Level : raid1
     Array Size : 478471808 (456.31 GiB 489.96 GB)
  Used Dev Size : 478471808 (456.31 GiB 489.96 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 4                                                                                                                                                                                                                                
    Persistence : Superblock is persistent                                                                                                                                                                                                         
                                                                                                                                                                                                                                                   
    Update Time : Sat Nov 13 23:47:19 2010                                                                                                                                                                                                         
          State : clean, degraded                                                                                                                                                                                                                  
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

           UUID : ed22eec3:6b241f7d:b5e98380:b1e09930 (local to host d668.gigenet.com)
         Events : 0.132536

    Number   Major   Minor   RaidDevice State
       2       8        4        0      spare rebuilding   /dev/sda4
       1       8       20        1      active sync   /dev/sdb4
```

As far as I can tell, that means that sda4 didn't sync correctly right?  I don't see how it could be bad as I've been running on it up until 2 days ago, and the other partitions are fine.  Any ideas on this?  Thanks.

edit:
After removing and re-adding sda4 to force it to resync, yet again, it gets around 55% done and then stops when this shows up in dmesg:
```
[216234.103031] raid1: Disk failure on sda4, disabling device.
[216234.103033] raid1: Operation continuing on 1 devices.

```

---

### Post by BobMUK on 2010-11-18
> [216234.103031] raid1: Disk failure on sda4, disabling device.
[216234.103033] raid1: Operation continuing on 1 devices.

You're getting so-far into the sync and RAID is reporting a disk failure, kicking the member out of the array.

Check /var/log/messages for any disk errors.

---

### Post by moparisthebest on 2010-12-02
I've done some more looking around and the problem actually seems to be due to a READ error, on the brand new drive (that is also the only drive with data on it :(), /dev/sdb:

```
$ grep -B10 -A10 "Unhandled sense code" /var/log/messages 
Dec  1 03:50:24 d668 kernel: [1286241.880775] ata2: EH complete
Dec  1 03:50:29 d668 kernel: [1286246.690371] ata2.00: configured for UDMA/100
Dec  1 03:50:29 d668 kernel: [1286246.690726] ata2: EH complete
Dec  1 03:50:34 d668 kernel: [1286251.500372] ata2.00: configured for UDMA/100
Dec  1 03:50:34 d668 kernel: [1286251.500664] ata2: EH complete
Dec  1 03:50:39 d668 kernel: [1286256.300370] ata2.00: configured for UDMA/100
Dec  1 03:50:39 d668 kernel: [1286256.300804] ata2: EH complete
Dec  1 03:50:44 d668 kernel: [1286261.130371] ata2.00: configured for UDMA/100
Dec  1 03:50:44 d668 kernel: [1286261.130758] ata2: EH complete
Dec  1 03:50:49 d668 kernel: [1286265.950373] ata2.00: configured for UDMA/100
Dec  1 03:50:49 d668 kernel: [1286265.950782] sd 1:0:0:0: [sdb] Unhandled sense code
Dec  1 03:50:49 d668 kernel: [1286265.950784] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec  1 03:50:49 d668 kernel: [1286265.950788] sd 1:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Dec  1 03:50:49 d668 kernel: [1286265.950793] Descriptor sense data with sense descriptors (in hex):
Dec  1 03:50:49 d668 kernel: [1286265.950795]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Dec  1 03:50:49 d668 kernel: [1286265.950803]         1e 86 46 5c 
Dec  1 03:50:49 d668 kernel: [1286265.950806] sd 1:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Dec  1 03:50:49 d668 kernel: [1286265.950811] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 1e 86 46 52 00 04 00 00
Dec  1 03:50:49 d668 kernel: [1286265.961225] ata2: EH complete
Dec  1 03:50:53 d668 kernel: [1286270.720373] ata2.00: configured for UDMA/100
Dec  1 03:50:53 d668 kernel: [1286270.720778] ata2: EH complete
Dec  1 03:50:58 d668 kernel: [1286275.490374] ata2.00: configured for UDMA/100
Dec  1 03:50:58 d668 kernel: [1286275.490804] ata2: EH complete
Dec  1 03:51:03 d668 kernel: [1286280.240370] ata2.00: configured for UDMA/100
Dec  1 03:51:03 d668 kernel: [1286280.240727] ata2: EH complete
Dec  1 03:51:08 d668 kernel: [1286285.042931] ata2.00: configured for UDMA/100
Dec  1 03:51:08 d668 kernel: [1286285.043312] ata2: EH complete
Dec  1 03:51:12 d668 kernel: [1286289.812874] ata2.00: configured for UDMA/100
Dec  1 03:51:12 d668 kernel: [1286289.813229] ata2: EH complete
Dec  1 03:51:17 d668 kernel: [1286294.570373] ata2.00: configured for UDMA/100
Dec  1 03:51:17 d668 kernel: [1286294.570787] sd 1:0:0:0: [sdb] Unhandled sense code
Dec  1 03:51:17 d668 kernel: [1286294.570790] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec  1 03:51:17 d668 kernel: [1286294.570794] sd 1:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Dec  1 03:51:17 d668 kernel: [1286294.570799] Descriptor sense data with sense descriptors (in hex):
Dec  1 03:51:17 d668 kernel: [1286294.570801]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Dec  1 03:51:17 d668 kernel: [1286294.570809]         1e 86 4b 98 
Dec  1 03:51:17 d668 kernel: [1286294.570812] sd 1:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Dec  1 03:51:17 d668 kernel: [1286294.570818] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 1e 86 4a 52 00 04 00 00
Dec  1 03:51:17 d668 kernel: [1286294.581115] ata2: EH complete
Dec  1 03:51:22 d668 kernel: [1286299.470358] ata2.00: configured for UDMA/100
Dec  1 03:51:22 d668 kernel: [1286299.470374] ata2: EH complete
Dec  1 03:51:27 d668 kernel: [1286304.292895] ata2.00: configured for UDMA/100
Dec  1 03:51:27 d668 kernel: [1286304.292912] ata2: EH complete
Dec  1 03:51:32 d668 kernel: [1286309.122856] ata2.00: configured for UDMA/100
Dec  1 03:51:32 d668 kernel: [1286309.122868] ata2: EH complete
Dec  1 03:51:37 d668 kernel: [1286313.940362] ata2.00: configured for UDMA/100
Dec  1 03:51:37 d668 kernel: [1286313.940382] ata2: EH complete
Dec  1 03:51:41 d668 kernel: [1286318.732862] ata2.00: configured for UDMA/100
Dec  1 03:51:41 d668 kernel: [1286318.732878] ata2: EH complete
Dec  1 03:51:46 d668 kernel: [1286323.552858] ata2.00: configured for UDMA/100
Dec  1 03:51:46 d668 kernel: [1286323.552878] sd 1:0:0:0: [sdb] Unhandled sense code
Dec  1 03:51:46 d668 kernel: [1286323.552880] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec  1 03:51:46 d668 kernel: [1286323.552884] sd 1:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Dec  1 03:51:46 d668 kernel: [1286323.552889] Descriptor sense data with sense descriptors (in hex):
Dec  1 03:51:46 d668 kernel: [1286323.552890]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Dec  1 03:51:46 d668 kernel: [1286323.552898]         1e 86 46 5c 
Dec  1 03:51:46 d668 kernel: [1286323.552902] sd 1:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Dec  1 03:51:46 d668 kernel: [1286323.552907] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 1e 86 46 5a 00 00 08 00
Dec  1 03:51:46 d668 kernel: [1286323.563308] ata2: EH complete
Dec  1 03:51:46 d668 kernel: [1286323.573919] md: md4: recovery done.
Dec  1 03:51:51 d668 kernel: [1286328.380356] ata2.00: configured for UDMA/100
Dec  1 03:51:51 d668 kernel: [1286328.380366] ata2: EH complete
Dec  1 03:51:56 d668 kernel: [1286333.172856] ata2.00: configured for UDMA/100
Dec  1 03:51:56 d668 kernel: [1286333.172868] ata2: EH complete
Dec  1 03:52:01 d668 kernel: [1286337.942858] ata2.00: configured for UDMA/100
Dec  1 03:52:01 d668 kernel: [1286337.942873] ata2: EH complete
Dec  1 03:52:05 d668 kernel: [1286342.680369] ata2.00: configured for UDMA/100
Dec  1 03:52:05 d668 kernel: [1286342.680379] ata2: EH complete
Dec  1 03:52:10 d668 kernel: [1286347.472859] ata2.00: configured for UDMA/100
Dec  1 03:52:10 d668 kernel: [1286347.472878] ata2: EH complete
Dec  1 03:52:15 d668 kernel: [1286352.222858] ata2.00: configured for UDMA/100
Dec  1 03:52:15 d668 kernel: [1286352.222877] sd 1:0:0:0: [sdb] Unhandled sense code
Dec  1 03:52:15 d668 kernel: [1286352.222879] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec  1 03:52:15 d668 kernel: [1286352.222883] sd 1:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
Dec  1 03:52:15 d668 kernel: [1286352.222888] Descriptor sense data with sense descriptors (in hex):
Dec  1 03:52:15 d668 kernel: [1286352.222890]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Dec  1 03:52:15 d668 kernel: [1286352.222898]         1e 86 4b 98 
Dec  1 03:52:15 d668 kernel: [1286352.222901] sd 1:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
Dec  1 03:52:15 d668 kernel: [1286352.222906] sd 1:0:0:0: [sdb] CDB: Read(10): 28 00 1e 86 4b 92 00 00 08 00
Dec  1 03:52:15 d668 kernel: [1286352.233125] ata2: EH complete

```

Does anyone have any ideas on going about fixing this problem? :confused:

---

### Post by James78 on 2010-12-02
Sometimes the only way to solve errors like that is to wipe everything and reinstall, then put all the files back and try again. Don't take my word for it though, someone may have a better idea. This is only last resort.

---

