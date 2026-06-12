---
title: "mdadm RAID recovery"
date: 2005-11-29
forum: Server Platforms
---

### Post by f1d094 on 2005-11-29
I have 4 SATA drives in RAID5 on a server that warm booted last night after problems with a mis-behaving application. Upon reboot, one of the drives came up faulty. I thought this was most likely due to the dirty reboot, so I simply hotadded it back in and went back to bed. In the morning, when I checked its status and was traumatized to see that the drive was now simply marked "spare" and *another* drive was also marked faulty.

Prior to this point, I was able to use the device (/dev/md0) normally, ableit in a degraded state. Now, I couldn't do anything.

After some homework, I found [this tidbit]("http://www.tldp.org/HOWTO/Software-RAID-HOWTO-8.html#ss8.1") and therefore tried "mdadm --assemble --force /dev/md0" and the device fired up just fine (with the original drive missing)...I again tried rebuilding and everything looked good until the 99% point...then /dev/sda3 went to "faulty" again....and /dev/sdb3 was never added to the array.

If I add a "fresh" drive" with /dev/sda3 in the mix, and then do the "mdadm --assemble --force" again I will receive similar results. But if I take out /dev/sda3 and leave in /dev/sdb3 I'm not certain I won't wind up with corrupt data.

I'm uncertain on how to proceed. The immediate availability of the system itself isn't critical, but data integrity is. I CANNOT afford to lose these data.

Below is supplemental info.

Thanks!!!

Here is the output from "mdadm -D /dev/md0" prior to hot-add:

```

/dev/md0:
       Version : 00.90.01
 Creation Time : Wed Apr 27 03:44:06 2005
    Raid Level : raid5
    Array Size : 725671872 (692.05 GiB 743.09 GB)
   Device Size : 241890624 (230.68 GiB 247.70 GB)
  Raid Devices : 4
 Total Devices : 4
Preferred Minor : 0
   Persistence : Superblock is persistent

   Update Time : Tue Nov 29 13:30:17 2005
         State : clean, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
 Spare Devices : 1

        Layout : left-symmetric
    Chunk Size : 64K

 Rebuild Status : 47% complete

          UUID : b22bea6d:62339cd7:0ce83b75:4ac59414
        Events : 0.8902455

   Number   Major   Minor   RaidDevice State
      0       8       51        0      active sync   /dev/sdd3
      1       8       35        1      active sync   /dev/sdc3
      2       0        0        -      removed
      3       8        3        3      active sync   /dev/sda3

      4       8       19        2      spare rebuilding   /dev/sdb3

```

Here is the output afterwards:

```

/dev/md0:
       Version : 00.90.01
 Creation Time : Wed Apr 27 03:44:06 2005
    Raid Level : raid5
    Array Size : 725671872 (692.05 GiB 743.09 GB)
   Device Size : 241890624 (230.68 GiB 247.70 GB)
  Raid Devices : 4
 Total Devices : 4
Preferred Minor : 0
   Persistence : Superblock is persistent

   Update Time : Wed Nov 30 00:45:01 2005
         State : clean, degraded
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
 Spare Devices : 1

        Layout : left-symmetric
    Chunk Size : 64K

          UUID : b22bea6d:62339cd7:0ce83b75:4ac59414
        Events : 0.8902461

   Number   Major   Minor   RaidDevice State
      0       8       51        0      active sync   /dev/sdd3
      1       8       35        1      active sync   /dev/sdc3
      2       0        0        -      removed
      3       0        0        -      removed

      4       8       19        -      spare   /dev/sdb3
      5       8        3        -      faulty   /dev/sda3

```

---

### Post by f1d094 on 2005-11-29
Here is the bottom end of syslog for the latest attempt to rebuild /dev/sdb3:

```

Nov 30 02:46:26 localhost kernel: [50638.961355] ata1: translated ATA stat/err 0x25/00 to SCSI SK/ASC/ASCQ 0x4/00/00
Nov 30 02:46:26 localhost kernel: [50638.961360] ata1: status=0x25 { DeviceFault CorrectedError Error }
Nov 30 02:46:26 localhost kernel: [50638.961379] SCSI error : <0 0 0 0> return code = 0x8000002
Nov 30 02:46:26 localhost kernel: [50638.961383] sda: Current: sense key: Hardware Error
Nov 30 02:46:26 localhost kernel: [50638.961385]     Additional sense: No additional sense information
Nov 30 02:46:26 localhost kernel: [50638.961390] end_request: I/O error, dev sda, sector 489794833
Nov 30 02:46:26 localhost kernel: [50638.994383] RAID5 conf printout:
Nov 30 02:46:26 localhost kernel: [50638.994387]  --- rd:4 wd:2 fd:2
Nov 30 02:46:26 localhost kernel: [50638.994390]  disk 0, o:1, dev:sdd3
Nov 30 02:46:26 localhost kernel: [50638.994392]  disk 1, o:1, dev:sdc3
Nov 30 02:46:26 localhost kernel: [50638.994395]  disk 2, o:1, dev:sdb3
Nov 30 02:46:26 localhost kernel: [50638.994397]  disk 3, o:0, dev:sda3
Nov 30 02:46:26 localhost kernel: [50638.996704] RAID5 conf printout:
Nov 30 02:46:26 localhost kernel: [50638.996707]  --- rd:4 wd:2 fd:2
Nov 30 02:46:26 localhost kernel: [50638.996709]  disk 0, o:1, dev:sdd3
Nov 30 02:46:26 localhost kernel: [50638.996711]  disk 1, o:1, dev:sdc3
Nov 30 02:46:26 localhost kernel: [50638.996714]  disk 3, o:0, dev:sda3
Nov 30 02:46:26 localhost kernel: [50638.996716] RAID5 conf printout:
Nov 30 02:46:26 localhost kernel: [50638.996718]  --- rd:4 wd:2 fd:2
Nov 30 02:46:26 localhost kernel: [50638.996720]  disk 0, o:1, dev:sdd3
Nov 30 02:46:26 localhost kernel: [50638.996722]  disk 1, o:1, dev:sdc3
Nov 30 02:46:26 localhost kernel: [50638.996724]  disk 3, o:0, dev:sda3
Nov 30 02:46:26 localhost kernel: [50638.999703] RAID5 conf printout:
Nov 30 02:46:26 localhost kernel: [50638.999705]  --- rd:4 wd:2 fd:2
Nov 30 02:46:26 localhost kernel: [50638.999707]  disk 0, o:1, dev:sdd3
Nov 30 02:46:26 localhost kernel: [50638.999710]  disk 1, o:1, dev:sdc3

```

---

