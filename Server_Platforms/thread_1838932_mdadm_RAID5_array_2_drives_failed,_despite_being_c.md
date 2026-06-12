---
title: "mdadm RAID5 array 2 drives failed, despite being clean, was able to re-assemble"
date: 2011-09-04
forum: Server Platforms
---

### Post by Kilbasar on 2011-09-04
Hi All,

I've got a 3 drive (sdb/sdc/sde) RAID5 array. Today, out of the blue, it stopped working, with 2/3 drives (sdb and sdc) showing as failed in the /prod/mdstat output. I have a cron job that checks this file every 5 minutes for failed drives, so they must have both failed at the same time, or at least within a very short time of each other. I rebooted, and mdadm would not let me rebuild the array:

```
# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdc[1](S) sdb[0](S) sde[2](S)
      5860543488 blocks
# mdadm /dev/md0 --assemble -u d7d529c7:fe947ccc:2a8727ae:e02361df
mdadm: metadata format 00.90 unknown, ignored.
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
```

The strange part is that all 3 drives showed up as "clean" in their examine output:

```
# mdadm --examine /dev/sdc
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d7d529c7:fe947ccc:2a8727ae:e02361df (local to host tet)
  Creation Time : Fri Feb  5 15:13:41 2010
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 3907028992 (3726.03 GiB 4000.80 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Sep  4 09:50:05 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 988502e4 - correct
         Events : 106562

         Layout : left-symmetric
     Chunk Size : 128K

      Number   Major   Minor   RaidDevice State
this     1       8       32        1      active sync   /dev/sdc

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       64        2      active sync   /dev/sde

# mdadm --examine /dev/sdb
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d7d529c7:fe947ccc:2a8727ae:e02361df (local to host tet)
  Creation Time : Fri Feb  5 15:13:41 2010
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 3907028992 (3726.03 GiB 4000.80 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Sep  4 09:50:05 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 988502d2 - correct
         Events : 106562

         Layout : left-symmetric
     Chunk Size : 128K

      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       64        2      active sync   /dev/sde

# mdadm --examine /dev/sde
mdadm: metadata format 00.90 unknown, ignored.
/dev/sde:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d7d529c7:fe947ccc:2a8727ae:e02361df (local to host tet)
  Creation Time : Fri Feb  5 15:13:41 2010
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 3907028992 (3726.03 GiB 4000.80 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Sep  4 13:25:12 2011
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 988535a7 - correct
         Events : 106580

         Layout : left-symmetric
     Chunk Size : 128K

      Number   Major   Minor   RaidDevice State
this     2       8       64        2      active sync   /dev/sde

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       64        2      active sync   /dev/sde

```

I was finally able to get the array working by forcing it to rebuild:

```
# mdadm --assemble /dev/md0 --scan --force
mdadm: metadata format 00.90 unknown, ignored.
mdadm: forcing event count in /dev/sdb(0) from 106562 upto 106580
mdadm: forcing event count in /dev/sdc(1) from 106562 upto 106580
mdadm: /dev/md0 has been started with 3 drives.
# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb[0] sde[2] sdc[1]
      3907028992 blocks level 5, 128k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>
```

I've since mounted the array, and it seems to work. Obviously my next step is running a full backup, and then doing some SMART tests. But I'm curious if anyone can tell what happened here? There's some interesting stuff in my dmesg output, which is below. Thanks!

```
[ 1234.144275] raid5: device sdb operational as raid disk 0
[ 1234.144277] raid5: device sde operational as raid disk 2
[ 1234.144279] raid5: device sdc operational as raid disk 1
[ 1234.144643] raid5: allocated 3230kB for md0
[ 1234.144919] 0: w=1 pa=0 pr=3 m=1 a=2 r=3 op1=0 op2=0
[ 1234.144922] 2: w=2 pa=0 pr=3 m=1 a=2 r=3 op1=0 op2=0
[ 1234.144924] 1: w=3 pa=0 pr=3 m=1 a=2 r=3 op1=0 op2=0
[ 1234.144926] raid5: raid level 5 set md0 active with 3 out of 3 devices, algorithm 2
[ 1234.144928] RAID5 conf printout:
[ 1234.144929]  --- rd:3 wd:3
[ 1234.144931]  disk 0, o:1, dev:sdb
[ 1234.144933]  disk 1, o:1, dev:sdc
[ 1234.144934]  disk 2, o:1, dev:sde
[ 1234.144963] md0: detected capacity change from 0 to 4000797687808
[ 1234.145152]  md0: unknown partition table
[ 1269.310042] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 1125
[ 1315.640187] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1315.640191] ata3.00: BMDMA stat 0x64
[ 1315.640195] ata3.00: failed command: READ DMA EXT
[ 1315.640199] ata3.00: cmd 25/00:08:a0:c2:42/00:00:e5:00:00/e0 tag 0 dma 4096 in
[ 1315.640200]          res 51/40:00:a0:c2:42/40:00:e5:00:00/e0 Emask 0x9 (media error)
[ 1315.640203] ata3.00: status: { DRDY ERR }
[ 1315.640205] ata3.00: error: { UNC }
[ 1315.701137] ata3.00: configured for UDMA/133
[ 1315.740816] ata3.01: configured for UDMA/133
[ 1315.740827] ata3: EH complete
[ 1318.607001] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1318.607005] ata3.00: BMDMA stat 0x64
[ 1318.607008] ata3.00: failed command: READ DMA EXT
[ 1318.607013] ata3.00: cmd 25/00:08:a0:c2:42/00:00:e5:00:00/e0 tag 0 dma 4096 in
[ 1318.607014]          res 51/40:00:a0:c2:42/40:00:e5:00:00/e0 Emask 0x9 (media error)
[ 1318.607017] ata3.00: status: { DRDY ERR }
[ 1318.607019] ata3.00: error: { UNC }
[ 1318.660352] ata3.00: configured for UDMA/133
[ 1318.700591] ata3.01: configured for UDMA/133
[ 1318.700602] ata3: EH complete
[ 1321.539775] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1321.539779] ata3.00: BMDMA stat 0x64
[ 1321.539782] ata3.00: failed command: READ DMA EXT
[ 1321.539787] ata3.00: cmd 25/00:08:a0:c2:42/00:00:e5:00:00/e0 tag 0 dma 4096 in
[ 1321.539788]          res 51/40:00:a0:c2:42/40:00:e5:00:00/e0 Emask 0x9 (media error)
[ 1321.539790] ata3.00: status: { DRDY ERR }
[ 1321.539792] ata3.00: error: { UNC }
[ 1321.571688] ata3.00: configured for UDMA/133
[ 1321.611577] ata3.01: configured for UDMA/133
[ 1321.611587] ata3: EH complete
[ 1331.227775] kjournald starting.  Commit interval 5 seconds
[ 1331.227786] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[ 1331.257008] EXT3 FS on md0, internal journal
[ 1331.257011] EXT3-fs: recovery complete.
[ 1331.274106] EXT3-fs: mounted filesystem with ordered data mode.
[ 1389.313787] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 982
[ 1509.311032] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 751
[ 1629.311291] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 982
[ 1749.310838] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 745
[ 1869.313798] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 608
[ 1989.312772] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 898
[ 2109.311290] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 982
[ 2229.310043] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 739
[ 2349.310038] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 703
[ 2469.313790] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 703
[ 2589.316697] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1308
[ 2709.306840] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 834
[ 2829.306180] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 745

```

---

### Post by cofko on 2012-01-07
I've had the same problem , 2 out of 4 RAID5 devices just got simultaneously removed . log content :
```
Jan  2 02:06:35 cofko kernel: [3675232.329828] lost page write due to I/O error on md0
Jan  2 02:06:35 cofko mdadm[1941]: Fail event detected on md device /dev/md0, component device /dev/sdb1
Jan  2 02:06:35 cofko mdadm[1941]: Fail event detected on md device /dev/md0, component device /dev/sdc1

```

I've run badblocks on all 4 drives and no problem.

after reboot RAID5 didn't assemble:
```
Jan  5 11:57:58 cofko mdadm[1991]: DeviceDisappeared event detected on md device /dev/md0
```

--examine showed on 2 devices that the other 2 were removed / faulty removed:
```
$ sudo mdadm --misc --query --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 73503d15:19b201cd:3eef23e0:337d7e47
  Creation Time : Sat Sep  4 14:09:08 2010
     Raid Level : raid5
  Used Dev Size : 976761472 (931.51 GiB 1000.20 GB)
     Array Size : 2930284416 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Jan  1 04:21:03 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 7e583c7f - correct
         Events : 59458

         Layout : left-symmetric
     Chunk Size : 128K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       49        3      active sync   /dev/sdd1

$ sudo mdadm --misc --query --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 73503d15:19b201cd:3eef23e0:337d7e47
  Creation Time : Sat Sep  4 14:09:08 2010
     Raid Level : raid5
  Used Dev Size : 976761472 (931.51 GiB 1000.20 GB)
     Array Size : 2930284416 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Jan  1 04:21:03 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 7e583c89 - correct
         Events : 59450

         Layout : left-symmetric
     Chunk Size : 128K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       49        3      active sync   /dev/sdd1

$ sudo mdadm --misc --query --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 73503d15:19b201cd:3eef23e0:337d7e47
  Creation Time : Sat Sep  4 14:09:08 2010
     Raid Level : raid5
  Used Dev Size : 976761472 (931.51 GiB 1000.20 GB)
     Array Size : 2930284416 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Jan  2 12:23:16 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 7e59ff48 - correct
         Events : 59458

         Layout : left-symmetric
     Chunk Size : 128K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       49        3      active sync   /dev/sdd1


$ sudo mdadm --misc --query --examine /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 73503d15:19b201cd:3eef23e0:337d7e47
  Creation Time : Sat Sep  4 14:09:08 2010
     Raid Level : raid5
  Used Dev Size : 976761472 (931.51 GiB 1000.20 GB)
     Array Size : 2930284416 (2794.54 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Jan  2 12:23:16 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 7e59ff56 - correct
         Events : 59458

         Layout : left-symmetric
     Chunk Size : 128K

      Number   Major   Minor   RaidDevice State
this     2       8       65        2      active sync   /dev/sde1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       49        3      active sync   /dev/sdd1

```

assemble didn't work
$ mdadm --assemble /dev/md0 --scan
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.

assemble with --force solved the problem :
$ mdadm --assemble /dev/md0 --scan --force
mdadm: forcing event count in /dev/sdb1(0) from 59450 upto 59458
mdadm: forcing event count in /dev/sdc1(1) from 59450 upto 59458
mdadm: /dev/md0 has been started with 4 drives.

---

### Post by rubylaser on 2012-01-08
What's the output of smartctl on the disks?  It looks like a media error (pending sectors or UDMA errors caused by a bad SATA head or cable) from the logs but tough to tell without SMART reports.

---

### Post by tylersontag on 2012-11-22
I'm getting the same problem, i have 3 drives that --examine all reports as being clean but when i try to assemble them one of the drives has flagged 
the other 2 as failed...   i tried -A /device --scan -F but i still get teh same error message

Also, at the same time, when i restart my computer, it keeps trying to boot to the RAID device, even though its never been the primary boot device... fortunatly i have the RAID in an external enclosure si o just power it down, boot, and power it up once the computer finishes booting from the correct drive... any suggestions?

---

### Post by rubylaser on 2012-11-22
The first step is to look at the SMART data for each disk.

```
smartctl -a /dev/sdX
```
Then look at the mdadm metadata info on each disk.

```
mdadm -E /dev/sd[bcd]
```
^ Obviously use the correct devices, this is just an example.

---

### Post by javaguru on 2013-06-29
> **tylersontag said:**
> I'm getting the same problem, i have 3 drives that --examine all reports as being clean but when i try to assemble them one of the drives has flagged 
the other 2 as failed...   i tried -A /device --scan -F but i still get teh same error message

Also, at the same time, when i restart my computer, it keeps trying to boot to the RAID device, even though its never been the primary boot device... fortunatly i have the RAID in an external enclosure si o just power it down, boot, and power it up once the computer finishes booting from the correct drive... any suggestions?

Did you ever get it to assemble correctly ? I have the exact same problem, and I've tried --assemble --scan --force and nothing .. All drives are clean

---

### Post by rubylaser on 2013-06-29
Can you provide the output of these?
```
cat /proc/mdstat
cat /etc/mdadm/mdadm.conf
```
and do this for each array disk (or partition)
```
mdadm -E /dev/sd[bcd]
# If you are using partitions
mdadm -E /dev/sd[bcd]1
```

---

