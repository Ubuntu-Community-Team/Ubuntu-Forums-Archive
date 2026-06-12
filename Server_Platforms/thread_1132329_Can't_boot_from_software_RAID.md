---
title: "Can't boot from software RAID"
date: 2009-04-21
forum: Server Platforms
---

### Post by annonemouse on 2009-04-21
Hello, all.

I am trying to install Ubuntu Server 8.10 onto a software RAID partition, pretty much exactly as described [here]("http://usefulubuntu.blogspot.com/2009/03/raid-1-and-ubuntu-server-810.html")
or [here]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/").

When I follow the steps in the above examples, everything goes according to plan, until the post-install reboot. Grub comes up fine, and the boot line looks correct:
```
  kernel		/boot/vmlinuz-2.6.27-7-server root=/dev/md0 ro
```
However, it seems that /dev/md0 fails to initialize (in time?) 
```
===========================
  ** WARNING: There appears to be one or more degraded RAID devices **
  md0 : inactive dm-1[0]S
        11719296 blocks
===========================
```
and the system fails to mount its root partition. 

I have tried installing with partition schemes identical to both examples above. But for simplicity's sake, I have reproduced this problem with just a single level-1 Software RAID, made from two bootable partitions on /dev/sda and /dev/sdb. Here are the partition tables from 'fdisk -l /dev/sd[ab]':
```
===========================
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005643b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   fd  Linux raid autodetect
===========================
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e75b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1459    11719386   fd  Linux raid autodetect
===========================
```


Here is the array in functional state, just after installation finishes, but before reboot:
```
===========================
/dev/md0:
        Version : 00.90
  Creation Time : Tue Apr 21 19:20:43 2009
     Raid Level : raid1
     Array Size : 11719296 (11.18 GiB 12.00 GB)
  Used Dev Size : 11719296 (11.18 GiB 12.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Apr 21 20:13:01 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 2ae5e7d8:756ca3ef:a9f80f90:989c9c16
         Events : 0.6

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
===========================

```

Here's the disk-related 'dmesg' output from the post-install reboot:
```
===========================
[    0.000000] Linux version 2.6.27-7-server (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 07:37:55 UTC 2008 (Ubuntu 2.6.27-7.14-server)
...
[    2.341964] md: linear personality registered for level -1
[    2.345525] md: multipath personality registered for level -4
[    2.348495] md: raid0 personality registered for level 0
[    2.353098] md: raid1 personality registered for level 1
...
[    2.570019] raid6: int32x1    952 MB/s
[    2.740013] raid6: int32x2    835 MB/s
[    2.910063] raid6: int32x4    677 MB/s
[    3.080026] raid6: int32x8    525 MB/s
[    3.250029] raid6: mmxx1     1612 MB/s
[    3.420016] raid6: mmxx2     2949 MB/s
[    3.590021] raid6: sse1x1    1656 MB/s
[    3.760016] raid6: sse1x2    2819 MB/s
[    3.930029] raid6: sse2x1    2807 MB/s
[    4.100008] raid6: sse2x2    3756 MB/s
[    4.100010] raid6: using algorithm sse2x2 (3756 MB/s)
[    4.100013] md: raid6 personality registered for level 6
[    4.100016] md: raid5 personality registered for level 5
[    4.100018] md: raid4 personality registered for level 4
[    4.123716] md: raid10 personality registered for level 10
...
[    5.691863] scsi0 : ahci
[    5.692252] scsi1 : ahci
[    5.692614] scsi2 : ahci
[    5.693001] scsi3 : ahci
[    5.693408] scsi4 : ahci
[    5.693836] scsi5 : ahci
[    5.693977] ata1: SATA max UDMA/133 abar m8192@0xfce76000 port 0xfce76100 irq 220
[    5.693981] ata2: SATA max UDMA/133 abar m8192@0xfce76000 port 0xfce76180 irq 220
[    5.693984] ata3: SATA max UDMA/133 abar m8192@0xfce76000 port 0xfce76200 irq 220
[    5.693987] ata4: SATA max UDMA/133 abar m8192@0xfce76000 port 0xfce76280 irq 220
[    5.693990] ata5: SATA max UDMA/133 abar m8192@0xfce76000 port 0xfce76300 irq 220
[    5.693993] ata6: SATA max UDMA/133 abar m8192@0xfce76000 port 0xfce76380 irq 220
...
[    6.221271] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.221801] ata1.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[    6.221805] ata1.00: 488397168 sectors, multi 0: LBA48 
[    6.222381] ata1.00: configured for UDMA/133
...
[    8.170040] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    8.170561] ata2.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[    8.170565] ata2.00: 488397168 sectors, multi 0: LBA48 
[    8.171168] ata2.00: configured for UDMA/133
...
[   10.170137] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[   10.170295] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
...
[   10.783346] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[   10.783390] scsi 1:0:0:0: Attached scsi generic sg1 type 0
...
[   10.851340] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   10.851364] sd 0:0:0:0: [sda] Write Protect is off
[   10.851367] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.851638] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.851724] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   10.851740] sd 0:0:0:0: [sda] Write Protect is off
[   10.851743] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   10.851771] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
...
[   10.861381]  sda1
[   10.861493] sd 0:0:0:0: [sda] Attached SCSI disk
[   10.861602] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   10.861634] sd 1:0:0:0: [sdb] Write Protect is off
[   10.861637] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   10.861691] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.861779] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   10.861807] sd 1:0:0:0: [sdb] Write Protect is off
[   10.861810] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   10.861862] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   10.861867]  sdb: sdb1
[   10.874433] sd 1:0:0:0: [sdb] Attached SCSI disk
[   10.874440] usbhid: v2.6:USB HID core driver
[   10.882219] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   10.882225] Uniform CD-ROM driver Revision: 3.20
[   10.882323] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   11.093502] md: md0 stopped.
[   11.109315] md: md0 stopped.
[   11.110706] md: bind<dm-1>
[   12.106162] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[001947cc72440000]
[   12.106302] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[0011066645557194]

===========================
```
That's actually the very end of dmesg output. "md: md0 stoped." Not so helpful.

When the boot sequence fails, a prompt appears at the console, offering to boot the RAID in a degraded state. If I say No (the default) an emergency console results. If I say Yes, the system boots, but using only one disk (I guess sda?). In either case, my limited experience with software RAID has not enabled me to figure out how to restore the RAID to normal operations. And even if I did, it seems likely the problem would recur on reboot -- though this is speculation on my part. 

I seem to have exactly the same problem as
[This poster]("http://ubuntuforums.org/showthread.php?t=917675").

I have tried adding "rootdelay=120" and "dmraid=false" to my boot command. Just waits longer, then produces the same error.
I welcome any ideas on how to troubleshoot or further diagnose.

Thanks in advance,
- Ann

---

### Post by xris_xcess on 2009-04-22
I suggest.

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

or the general search "RAID" @ [https://help.ubuntu.com/search.html](https://help.ubuntu.com/search.html).

I followed the instructions in the first link to get my RAID1 server setup up and running (for a year now, no problems).

I believe the tricky part is adding the raid modules to the initramfs, rebuilding it, and then a small "tweak" to the rcS scripts. I see these are not in the guides you followed... that might be the reason for the pickle .-)

---

