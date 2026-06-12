---
title: "Slow response - RAID problem?"
date: 2019-09-13
forum: Server Platforms
---

### Post by gus_zernial on 2019-09-13
I'm getting slow/delayed response on a Kubuntu 19.04 system. The home directory is on a software two disk RAID1, see below. I see a lot of errors on one of the RAID disks, and resync is taking forever, also see below. My questions are:

-Is it likely that the sdb errors are what's causing delayed response, and/or how do I further diagnose?

-If the disk is the problem, I'm perfectly willing to replace the disk, or both disks for that matter, since they're both the same age, but ... are there things
I should do/try first?

I'm somewhere between a novice and an expert, but this problem is at the edge of my capabilities to diagnose/fix, so recommendations to diagnose and fix appreciated .... Gus

$ mdadm --detail /dev/md0
/dev/md0:
           Version : 1.2
     Creation Time : Fri Aug 19 08:34:54 2016
        Raid Level : raid1
        Array Size : 1829867904 (1745.10 GiB 1873.78 GB)
     Used Dev Size : 1829867904 (1745.10 GiB 1873.78 GB)
      Raid Devices : 2
     Total Devices : 2
       Persistence : Superblock is persistent

     Intent Bitmap : Internal

       Update Time : Fri Sep 13 11:21:49 2019
             State : active, resyncing 
    Active Devices : 2
   Working Devices : 2
    Failed Devices : 0
     Spare Devices : 0

Consistency Policy : bitmap

     Resync Status : 0% complete

              Name : Jboat17:0  (local to host Jboat17)
              UUID : cfde6372:28fef717:4d35e851:bbf99b6b
            Events : 87151

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8        1        1      active sync   /dev/sda1


And I'm getting a lot of these ............

$ tail -f /var/log/kern.log

Sep 13 11:12:44 Jboat17 kernel: [ 2585.835973] ata2.00: exception Emask 0x0 SAct 0x407400 SErr 0x0 action 0x0
Sep 13 11:12:44 Jboat17 kernel: [ 2585.835980] ata2.00: irq_stat 0x40000008
Sep 13 11:12:44 Jboat17 kernel: [ 2585.835986] ata2.00: failed command: READ FPDMA QUEUED
Sep 13 11:12:44 Jboat17 kernel: [ 2585.835997] ata2.00: cmd 60/00:60:80:75:79/05:00:00:00:00/40 tag 12 ncq dma 655360 in
Sep 13 11:12:44 Jboat17 kernel: [ 2585.835997]          res 41/40:00:70:78:79/00:00:00:00:00/40 Emask 0x409 (media error) <F>
Sep 13 11:12:44 Jboat17 kernel: [ 2585.836001] ata2.00: status: { DRDY ERR }
Sep 13 11:12:44 Jboat17 kernel: [ 2585.836005] ata2.00: error: { UNC }
Sep 13 11:12:44 Jboat17 kernel: [ 2585.837278] ata2.00: configured for UDMA/133
Sep 13 11:12:44 Jboat17 kernel: [ 2585.837330] sd 1:0:0:0: [sdb] tag#12 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 13 11:12:44 Jboat17 kernel: [ 2585.837335] sd 1:0:0:0: [sdb] tag#12 Sense Key : Medium Error [current] 
Sep 13 11:12:44 Jboat17 kernel: [ 2585.837339] sd 1:0:0:0: [sdb] tag#12 Add. Sense: Unrecovered read error - auto reallocate failed
Sep 13 11:12:44 Jboat17 kernel: [ 2585.837344] sd 1:0:0:0: [sdb] tag#12 CDB: Read(10) 28 00 00 79 75 80 00 05 00 00
Sep 13 11:12:44 Jboat17 kernel: [ 2585.837348] print_req_error: I/O error, dev sdb, sector 7960688 flags 4000
Sep 13 11:12:44 Jboat17 kernel: [ 2585.837376] ata2: EH complete

And resync is taking forever ....

$ sudo watch cat /proc/mdstat

Every 2.0s: cat /proc/mdstat  
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda1[1] sdb1[0]
      1829867904 blocks super 1.2 [2/2] [UU]
      [>....................]  resync =  0.3% (5731456/1829867904) finish=7975.9min speed=3811K/sec
      bitmap: 14/14 pages [56KB], 65536KB chunk

unused devices: <none>

---

### Post by TheFu on 2019-09-13
Looks like a bad cable on one of the disks or a failing controller port.  I'd take the array off line. It looks likely that corrupted data is being written.

Raw SMART data would be helpful on both disks.  **smartctl** is the tool.  
Step 1 - run the tests on each disk first. Wait for the tests to finish.
Step 2 - run the report on each disk.  Look at the raw data.

You can lookup each of the SMART values for what they mean.


Oh and if you don't already have backups, YOU NEED SOME ASAP.

---

