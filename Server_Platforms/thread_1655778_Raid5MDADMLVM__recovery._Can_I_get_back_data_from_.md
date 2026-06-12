---
title: "Raid5MDADM/LVM  recovery. Can I get back data from disks which I have used pvmove on?"
date: 2010-12-30
forum: Server Platforms
---

### Post by lotharz0r on 2010-12-30
Hi.
-----------
If you just want to read the questions, scroll to the bottom.
I have included what I think may be useful of logs and other events before the error occured.
-----------

I used to have 3 raid 5 arrays consisting of 4 disks each.
md0 and md1 had old 250GB disks, 8 in total.

So I decided to buy 4 new 2TB disks to replace these 8 250GB disks.

md3 is 4 750GB disks, this array I want to keep.
All these 3 raid arrays are member of a volume group which I have called "raid5".

Not having enough SATA ports to have all disks connected at the same time, I connected one of the new 2TB disks, and joined it to the Volume Group. This disk was called /dev/sdb

Then I used pvmove on /dev/md0 and /dev/md1, reduced the volume group and used pvremove
> 
vgreduce -v raid5 /dev/md0
vgreduce -v raid5 /dev/md1
prvemove /dev/md0
pvremove /dev/md1


Now all of my data that previously was on md0 and md1 was on sdb1
After this was done, I shut down my server, disconnected 8 old hard drives and connected 3 more of the 2 TB drives, now having a total of 4 2TB drives.

I now created a new raid5 array with one drive missing, joined it to the Volume Group and used pvmove again to move data from sdb1 to the new md0 array.

This also went fine, so again I reduced the Volume Group, removing sdb1.
> 
vgreduce -v raid5 /dev/sdb1
pvremove /dev/sdb1


I repartitioned /dev/sdb1 to be a linux raid device and added it to /dev/md0 with
> 
mdadm --manage --add /dev/md0 /dev/sdb1


Rebuilding now started, I watched /proc/mdstat for a couple of minutes, then went to do other things.

When I came back several hours later, the process had failed.

I found these messages in /var/log/messages
> 
Dec 29 18:58:31 terra kernel: [189488.988568] ata4: hard resetting link
Dec 29 18:58:32 terra kernel: [189490.024056] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 29 18:58:32 terra kernel: [189490.041246] ata4.00: configured for UDMA/33
Dec 29 18:58:32 terra kernel: [189490.041266] sd 3:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 29 18:58:32 terra kernel: [189490.041270] sd 3:0:0:0: [sdd] Sense Key : Aborted Command [current] [descriptor]
Dec 29 18:58:32 terra kernel: [189490.041276] Descriptor sense data with sense descriptors (in hex):
Dec 29 18:58:32 terra kernel: [189490.041279]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Dec 29 18:58:32 terra kernel: [189490.041292]         00 00 00 00 
Dec 29 18:58:32 terra kernel: [189490.041297] sd 3:0:0:0: [sdd] Add. Sense: No additional sense information
Dec 29 18:58:32 terra kernel: [189490.041302] sd 3:0:0:0: [sdd] CDB: Read(10): 28 00 e7 ab b5 00 00 01 00 00
Dec 29 18:58:32 terra kernel: [189490.041320] __ratelimit: 118 callbacks suppressed
Dec 29 18:58:32 terra kernel: [189490.041323] raid5:md0: read error not correctable (sector 3886300672 on sdd1).
Dec 29 18:58:32 terra kernel: [189490.041327] raid5:md0: read error not correctable (sector 3886300680 on sdd1).
Dec 29 18:58:32 terra kernel: [189490.041331] raid5:md0: read error not correctable (sector 3886300688 on sdd1).
Dec 29 18:58:32 terra kernel: [189490.041335] raid5:md0: read error not correctable (sector 3886300696 on sdd1).
Dec 29 18:58:32 terra kernel: [189490.041338] raid5:md0: read error not correctable (sector 3886300704 on sdd1).
Dec 29 18:58:32 terra kernel: [189490.041342] raid5:md0: read error not correctable (sector 3886300712 on sdd1).
Dec 29 18:58:32 terra kernel: [189490.041345] raid5:md0: read error not correctable (sector 3886300720 on sdd1).
Dec 29 18:58:32 terra kernel: [189490.041348] raid5:md0: read error not correctable (sector 3886300728 on sdd1).
Dec 29 18:58:32 terra kernel: [189490.041352] raid5:md0: read error not correctable (sector 3886300736 on sdd1).
Dec 29 18:58:32 terra kernel: [189490.041355] raid5:md0: read error not correctable (sector 3886300744 on sdd1).
Dec 29 18:58:32 terra kernel: [189490.041389] ata4: EH complete
Dec 29 18:59:03 terra kernel: [189520.988065] ata4: hard resetting link
Dec 29 18:59:03 terra kernel: [189521.464053] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 29 18:59:03 terra kernel: [189521.481254] ata4.00: configured for UDMA/33
Dec 29 18:59:03 terra kernel: [189521.481268] ata4: EH complete
Dec 29 18:59:34 terra kernel: [189551.988065] ata4: hard resetting link
Dec 29 18:59:34 terra kernel: [189552.744047] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 29 18:59:35 terra kernel: [189552.761100] ata4.00: configured for UDMA/33
Dec 29 18:59:35 terra kernel: [189552.761115] ata4: EH complete
Dec 29 19:00:05 terra kernel: [189582.988577] ata4: hard resetting link
Dec 29 19:00:05 terra kernel: [189583.520062] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 29 19:00:05 terra kernel: [189583.536441] ata4.00: configured for UDMA/33
Dec 29 19:00:05 terra kernel: [189583.536455] ata4: EH complete
Dec 29 19:00:36 terra kernel: [189613.988064] ata4: hard resetting link
Dec 29 19:00:37 terra kernel: [189615.080048] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 29 19:00:37 terra kernel: [189615.096568] ata4.00: configured for UDMA/33
Dec 29 19:00:37 terra kernel: [189615.096581] ata4: EH complete
Dec 29 19:01:08 terra kernel: [189645.988568] ata4: hard resetting link
Dec 29 19:01:08 terra kernel: [189646.464550] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 29 19:01:08 terra kernel: [189646.480522] ata4.00: configured for UDMA/33
Dec 29 19:01:08 terra kernel: [189646.480536] ata4: EH complete
Dec 29 19:01:39 terra kernel: [189676.988064] ata4: hard resetting link
Dec 29 19:01:40 terra kernel: [189677.968560] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 29 19:01:40 terra kernel: [189677.984592] ata4.00: configured for UDMA/33
Dec 29 19:01:40 terra kernel: [189677.984623] sd 3:0:0:0: [sdd] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 29 19:01:40 terra kernel: [189677.984627] sd 3:0:0:0: [sdd] Sense Key : Aborted Command [current] [descriptor]
Dec 29 19:01:40 terra kernel: [189677.984633] Descriptor sense data with sense descriptors (in hex):
Dec 29 19:01:40 terra kernel: [189677.984636]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Dec 29 19:01:40 terra kernel: [189677.984649]         00 00 00 00 
Dec 29 19:01:40 terra kernel: [189677.984654] sd 3:0:0:0: [sdd] Add. Sense: No additional sense information
Dec 29 19:01:40 terra kernel: [189677.984659] sd 3:0:0:0: [sdd] CDB: Read(10): 28 00 e7 ab b6 00 00 03 00 00
Dec 29 19:01:40 terra kernel: [189677.984677] __ratelimit: 22 callbacks suppressed
ec 29 19:01:40 terra kernel: [189677.984680] raid5:md0: read error not correctable (sector 3886300928 on sdd1).
Dec 29 19:01:40 terra kernel: [189677.984685] raid5:md0: read error not correctable (sector 3886300936 on sdd1).
Dec 29 19:01:40 terra kernel: [189677.984689] raid5:md0: read error not correctable (sector 3886300944 on sdd1).
Dec 29 19:01:40 terra kernel: [189677.984692] raid5:md0: read error not correctable (sector 3886300952 on sdd1).
Dec 29 19:01:40 terra kernel: [189677.984696] raid5:md0: read error not correctable (sector 3886300960 on sdd1).
Dec 29 19:01:40 terra kernel: [189677.984700] raid5:md0: read error not correctable (sector 3886300968 on sdd1).
Dec 29 19:01:40 terra kernel: [189677.984703] raid5:md0: read error not correctable (sector 3886300976 on sdd1).
Dec 29 19:01:40 terra kernel: [189677.984707] raid5:md0: read error not correctable (sector 3886300984 on sdd1).
Dec 29 19:01:40 terra kernel: [189677.984711] raid5:md0: read error not correctable (sector 3886300992 on sdd1).
Dec 29 19:01:40 terra kernel: [189677.984714] raid5:md0: read error not correctable (sector 3886301000 on sdd1).
Dec 29 19:01:40 terra kernel: [189677.984803] ata4: EH complete
Dec 29 19:01:40 terra kernel: [189678.320639] md: md0: recovery done.
Dec 29 19:01:40 terra kernel: [189678.367564] RAID5 conf printout:
Dec 29 19:01:40 terra kernel: [189678.367569]  --- rd:4 wd:2
Dec 29 19:01:40 terra kernel: [189678.367573]  disk 0, o:1, dev:sda1
Dec 29 19:01:40 terra kernel: [189678.367575]  disk 1, o:1, dev:sdb1
Dec 29 19:01:40 terra kernel: [189678.367578]  disk 2, o:1, dev:sdc1
Dec 29 19:01:40 terra kernel: [189678.367580]  disk 3, o:0, dev:sdd1
Dec 29 19:01:40 terra kernel: [189678.376547] RAID5 conf printout:
Dec 29 19:01:40 terra kernel: [189678.376552]  --- rd:4 wd:2
Dec 29 19:01:40 terra kernel: [189678.376556]  disk 0, o:1, dev:sda1
Dec 29 19:01:40 terra kernel: [189678.376559]  disk 2, o:1, dev:sdc1
Dec 29 19:01:40 terra kernel: [189678.376562]  disk 3, o:0, dev:sdd1
Dec 29 19:01:40 terra kernel: [189678.376573] RAID5 conf printout:
Dec 29 19:01:40 terra kernel: [189678.376575]  --- rd:4 wd:2
Dec 29 19:01:40 terra kernel: [189678.376577]  disk 0, o:1, dev:sda1
Dec 29 19:01:40 terra kernel: [189678.376580]  disk 2, o:1, dev:sdc1
Dec 29 19:01:40 terra kernel: [189678.376582]  disk 3, o:0, dev:sdd1
Dec 29 19:01:40 terra kernel: [189678.385386] RAID5 conf printout:
Dec 29 19:01:40 terra kernel: [189678.385391]  --- rd:4 wd:2
Dec 29 19:01:40 terra kernel: [189678.385395]  disk 0, o:1, dev:sda1
Dec 29 19:01:40 terra kernel: [189678.385398]  disk 2, o:1, dev:sdc1



So because of a read error on /dev/sdd1 I ended up with this array:
> 
root@terra:/var/log# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Mon Dec 27 14:59:29 2010
     Raid Level : raid5
     Array Size : 5859791424 (5588.33 GiB 6000.43 GB)
  Used Dev Size : 1953263808 (1862.78 GiB 2000.14 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Dec 30 09:32:41 2010
          State : clean, degraded
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 23b2fbd0:ed2ab11e:dd82fa75:dbadf535 (local to host terra)
         Events : 0.21074

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed
       2       8       33        2      active sync   /dev/sdc1
       3       0        0        3      removed

       4       8       17        -      spare   /dev/sdb1
       5       8       49        -      faulty spare   /dev/sdd1



According to smartmontools there is no problems with /dev/sdd1
> SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   173   170   021    Pre-fail  Always       -       6333
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       12
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       67
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       10
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       9
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       204
194 Temperature_Celsius     0x0022   123   120   000    Old_age   Always       -       27
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]



mdadm --examine show the same output as mdadm -D /dev/md0 on sda, sdb and sdc, but not sdd
> root@terra:/var/log# mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 23b2fbd0:ed2ab11e:dd82fa75:dbadf535 (local to host terra)
  Creation Time : Mon Dec 27 14:59:29 2010
     Raid Level : raid5
  Used Dev Size : 1953263808 (1862.78 GiB 2000.14 GB)
     Array Size : 5859791424 (5588.33 GiB 6000.43 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Dec 29 18:52:20 2010
          State : active
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 81dbc114 - correct
         Events : 21053

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       0        0        1      faulty removed
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       17        4      spare   /dev/sdb1


So there you have some background information.
I have two questions.

1. The disks all seem healthy. Can I "unfail" /dev/sdd1 and try to rebuild again? The read errors on /dev/sdd1 is maybe because of bad power splitters, or something, since smartmontools says the disk is OK.
I have read a lot about similar problems, and see someone has tried regenerating the array. In my case I used this command to create the array in the first place
> mdadm --create /dev/md0 --level 5 -n 4 /dev/sda1 missing /dev/sdc1 /dev/sdd1

Since the data on the hard drives probably is intact, can I use this command to get the array back in "active, degraded" state?
Should I delete /dev/md0 first?

Is it better to use this guide?[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)


Question 2:
Can I get data from the old hard drives I have pvmoved data from in the beginning?
I still have the 8 old disks from the old raid5 arrays, and they have not been used for anything else.
Can I recover the arrays and restore a backup of the LVM config to get the data back from there?
Do I need to know the exact order of the drives to salvage the mdadm raid array from these old drives?
Is it even possible to get back a deleted mdadm array?

---

