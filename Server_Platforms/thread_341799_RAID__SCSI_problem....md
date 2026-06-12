---
title: "RAID / SCSI problem..."
date: 2007-01-19
forum: Server Platforms
---

### Post by tomBorgia on 2007-01-19
Hi there, I've recently installed ubuntu-server on a (reasonably old) IBM server. It was working fine for a day or so, when I rebooted the server (after messing around with munin - which I don't think caused the problem but its a possiblity) I get the following system email -

This is an automatically generated mail message from mdadm
running on minas-tirith.citylinkleeds.co.uk

A DegradedArray event had been detected on md device /dev/md0.

Faithfully yours, etc.

So I had a look at the system messages from the boot process -

Jan 19 11:36:07 minas-tirith kernel: [42949419.270000] SCSI device sda: 35548320 512-byte hdwr sectors (18201 MB)
Jan 19 11:36:07 minas-tirith kernel: [42949419.340000] SCSI device sda: drive cache: write through
Jan 19 11:36:07 minas-tirith kernel: [42949419.370000] SCSI device sda: 35548320 512-byte hdwr sectors (18201 MB)
Jan 19 11:36:07 minas-tirith kernel: [42949419.430000] SCSI device sda: drive cache: write through
Jan 19 11:36:07 minas-tirith kernel: [42949419.430000]  sda:<3>ldm_parse_privhead(): Cannot find PRIVHEAD structure. LDM database is corrupt. Aborting.
Jan 19 11:36:07 minas-tirith kernel: [42949419.430000]  unable to read partition table

The other 3 disks are fine.

I had a look at this thread [http://www.linuxquestions.org/questions/showthread.php?t=475053](http://www.linuxquestions.org/questions/showthread.php?t=475053) which seems to think this is a hardware failure so I had a look at [http://tldp.net/HOWTO/html_single/Software-RAID-HOWTO/#ss6.3](http://tldp.net/HOWTO/html_single/Software-RAID-HOWTO/#ss6.3) - it suggested runnind mdadm --detail -

root@minas-tirith:/etc# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Jan 18 08:01:35 2007
     Raid Level : raid1
     Array Size : 17762112 (16.94 GiB 18.19 GB)
    Device Size : 17762112 (16.94 GiB 18.19 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jan 19 11:55:47 2007
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 55d8e930:361f6300:926c7859:ea592f62
         Events : 0.4157

    Number   Major   Minor   RaidDevice State
       0       0        0        -      removed
       1       8       17        1      active sync   /dev/sdb1

Further down the page it suggested to run this - mdadm /dev/md0 -a /dev/sda1

root@minas-tirith:/etc# mdadm /dev/md0 -a /dev/sda1
mdadm: cannot find /dev/sda1: No such file or directory

So is the drive knackerd, or is there something obvious I'm missing?!!

---

### Post by tomBorgia on 2007-01-24
Couldn't get this to fix but def not a hardware failure - I installed a hw raid controller and was able to use all the drives.

Tom.

---

