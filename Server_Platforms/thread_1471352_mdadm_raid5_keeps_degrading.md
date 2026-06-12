---
title: "mdadm raid5 keeps degrading"
date: 2010-05-03
forum: Server Platforms
---

### Post by mrjvp on 2010-05-03
Hi I'm a newby with linux but learning fast. Created my own file server/nas, but get stuck in a problem after couple of months.
I have a server with 4x 1,5tb disks, all connected to sata ports and 1 40gb ata133 disk running ubuntu 9.10 x64 amd. I've created a raid5 array using mdadm. It all worked great for couple of months but lately the raid5 array is degraded. disk sdd1 is faulting every few days. I have checked the drive but it is fine. If I re-add the disk and wait for 6 hours my raid5 array is all fine again, but after a few shutdowns, it is degraded. 

Here I post my mdadm detail:

> root@ubuntu: sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Mon Dec 14 13:00:43 2009
     Raid Level : raid5
     Array Size : 4395407808 (4191.79 GiB 4500.90 GB)
  Used Dev Size : 1465135936 (1397.26 GiB 1500.30 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon May  3 20:19:43 2010
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 4caba97c:0c88c8ad:e368bf24:bd0fce41 (local to host ubuntu)
         Events : 0.28361

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       0        0        3      removedI don't lose any data, but I'm afraid I will lose datd, when another disk is failing. So please help me to find the error.

Thx

---

### Post by tgalati4 on 2010-05-03
Did you load smartmontools to monitor the disk hardware?  You could be having a subtle failure of disk drive.

Also:

dmesg | grep error

Any disk/device errors?

---

### Post by mrjvp on 2010-05-04
I get this error, don't know what it means.
[    8.291970] amd64_edac: probe of 0000:00:18.2 failed with error -22

---

### Post by tgalati4 on 2010-05-04
amd64 is the 64-bit code base and edac is the module for ECC memory.  The kind you find in real server motherboards.  You don't have ECC memory or your motherboard doesn't support it.  No worries.  If you had ECC memory, you would get a few lines about how much ECC parameters, otherwise:

[ 8.801371] EDAC amd64: This node reports that Memory ECC is currently disabled.
[ 8.801378] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[ 8.801382] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[ 8.801384] Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[ 8.801386] Might be a BIOS bug, if BIOS says ECC is enabled
[ 8.801387] Use of the override can cause unknown side effects.
[ 8.801409] amd64_edac: probe of 0000:00:18.2 failed with error -22 

Try paging through your dmesg file and look for disk read errors:

dmesg | more

(spacebar to page forward, q to quit)

Take note of any strange entries.

Install smartmontools:

sudo apt-get install smartmontools

Get the status of your hard disks:

sudo smartctl -a /dev/sda
sudo smartctl -a /dev/sdb
.
.
.
etc.

It could be a power supply issue or a heat issue.  Pay attention to the temperature of sdd1 compared to the other drives.  When drives heat up, their compensation mechanisms can hit a limit leading to read errors and hence falling out of the RAID.

---

### Post by mrjvp on 2010-05-05
With smart tools I get the following output

> sudo smartctl -a /dev/sdd1
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD154UI
Serial Number:    S1Y6J9BSA05992
Firmware Version: 1AG01118
User Capacity:    1,500,301,910,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3b
Local Time is:    Wed May  5 11:56:27 2010 CEST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                 (19285) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (  34) minutes.
SCT capabilities:              (0x003f) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   072   072   011    Pre-fail  Always       -       9270
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       76
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       2231
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       75
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       0
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       115
184 Unknown_Attribute       0x0033   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   065   065   000    Old_age   Always       -       35 (Lifetime Min/Max 31/35)
194 Temperature_Celsius     0x0022   063   063   000    Old_age   Always       -       37 (Lifetime Min/Max 31/37)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       14639
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   253   253   000    Old_age   Always       -       122
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

Are there any values that could be the problem?

---

### Post by tgalati4 on 2010-05-05
Well, the SMART parameters look OK.  The temperature (35-37C) is normal.  You want to keep it below 45C.

You have not performed a self-test on this drive.  It will take a while:

Total time to complete Offline
data collection: (19285) seconds.
Offline data collection

Your drive hasn't collected any self-test data.  You can run a self-test while running (man smartctl for how to do it), but it will slow down your system until it finishes.

Are there any mdadm error messages in /var/log?

Also, look for previous errors in the various log files in /var/log.  Your current dmesg didn't show any disk errors.

So the disk looks OK.  I presume that the SMART parameters for the other disks are OK as well.

What type of power supply and how old is it?
When was the last time you cleaned out the machine and reseated all the connectors?
Do you have a beefy UPS on this machine?

My thinking is that without a battery-backed cache--the kind you find in a real RAID card, you run the risk of "memory holes".  Small dropouts of data that are recoverable but can lead to rebuilding events.

Put your finger on the SATA controller chip while it is running.  If it's toasty (meaning you can't keep your finger on it for 30 seconds), then you might need more cooling.  Also, try moving the SATA cables around.  Mark them with a Sharpie.  The cables are crimped (and who knows what kind of quality?) and all it takes is one marginal one to bring down your array.

If you move your cables and say /dev/sdb goes down, then take note of that cable.  RAID5 really pushes inter-disk communication and the cables and controller can be the weak point.  Again, a real RAID card tends to be beefier for sustained workloads.

Is the RAID fallout happening without load or does it happen after massive file movements?

If this NAS is simply for home use, I would question RAID usage in the first place.  It's not like you are handling airline ticket sales 24/7.  If it's for static storage of media, then RAID may be overkill.

RAID for home usage seems like a good idea on paper, but it can suck in practice.
Unlike wikipedia.

---

### Post by mrjvp on 2010-05-05
Thanks for all the effort you're putting in my problem. I use my server at homed for fileserver (storage and backup). So I've chosen a Raid5 array to be safe. I thought about no Raid at all, but lost all my data once and never want that to happen again. 

I checked all cabling and other hardware stuff you mentioned. It's a brand new machine bought in december 2009. All new harddisks, mainboard, memory etc. I have a bequit PSU with 380W power output for 4 SATA2 drives, 1 ATA drive and a mainboard.

Sometimes my server is online for 7 days, sometimes for just 12 hours. When the server and mdadm came online clean and working there was no problem whatsoever. So I think it has to do something between powering the machine off and turning it back on. 

I just made a backup for all files, so I can test all kinds off things. I will post my progress / results.

---

### Post by tgalati4 on 2010-05-06
RAID5 gives you striping performance and roving checksum protection, but it also puts stress on your SATA controller since it has to manage both the striping and checksum duties.  Do you have an UPS on this system?  If not, then simple power dips can cause data loss.  Without a real RAID controller, one that has a small backup battery to push the cache out to disk, you may experience hiccups.

There are lots of strategies for home server backup and performance.  You have to weigh all of the parameters.  I have never gotten SATA software RAID to work reliably for more than 1 year.  Now real server hardware with a real RAID card, those systems can go for years before a drive seizes up.

Also, if these are consumer Samsung drives (as opposed to enterprise-class Seagate or Western Digital drives) then you have to break them in to get reliable performance anyway.  Try running badblocks on each drive.  That will warm them up.

sudo badblocks /dev/sda

It's non-destructive, but it takes a lot of time.

---

### Post by windependence on 2010-05-06
> **mrjvp said:**
> Thanks for all the effort you're putting in my problem. I use my server at homed for fileserver (storage and backup). So I've chosen a Raid5 array to be safe. I thought about no Raid at all, but lost all my data once and never want that to happen again. 

I checked all cabling and other hardware stuff you mentioned. It's a brand new machine bought in december 2009. All new harddisks, mainboard, memory etc. I have a bequit PSU with 380W power output for 4 SATA2 drives, 1 ATA drive and a mainboard.

Sometimes my server is online for 7 days, sometimes for just 12 hours. When the server and mdadm came online clean and working there was no problem whatsoever. So I think it has to do something between powering the machine off and turning it back on. 

I just made a backup for all files, so I can test all kinds off things. I will post my progress / results.
FYI, RAID is no substitute for good backups. In the time it took you to set up software RAID you could have set up rsync and had regular backups going all the time. My backup strategy includes a separate drive (or two) where my data gets rsynced every hour or so. Real simple, but highly valuable. 

As was suggested you may have more luck with a real RAID controller with battery backup, but this STILL isn't a substitute for backups.

-Tim

---

### Post by TheDauthi on 2010-05-06
Are all of the drives Samsung and of the same firmware?

Last year, I had a nasty problem with an array degrading randomly, with no smart errors and nothing useful to note from dmesg.  After much trial and error, I found it was because I had different firmware versions on a fairly cheap SATA card.  It would degrade suddenly, sometimes having run under heavy load for hours, other times having simply booted.

Turns out I had a timing problem: one set of drives was responding to a set of commands much faster than the other set.  I don't think that's usually a problem, but my SATA card decided it was, and would reset the link and re-initialize.  Which mdadm recognized as a type of drive failure, and would mark the drive failed.

I upgraded the firmware on all 5 drives.  Array has been running smoothly for almost a year.

I bought all 5 drives at the same time, btw, so that's not a sure indicator that you're running the same stuff.  Also, be careful with your data until you get it fixed.  If you lose 2 drives, mdadm will be very unhappy.  It's recoverable, but I had a lot of problems with it.  And as said above, RAID5 is for high-availability, not backups of important data.

---

### Post by tgalati4 on 2010-05-06
That explains the random behavior for software RAID and consumer drives.  Yes, rsync is your friend.

---

### Post by mrjvp on 2010-05-07
Yes, I know RAID is not a backup solution, butit was working well enough for me. I have 1TB off my most important data on a removable drive. 

Yesterday mdadm tried to rebuild again, but it foulted around 25%. Now also SDA1 was creating problems. So I removed all superblocks and I am now creating a RAID10 set. It takes ages to build (still 320 minutes remaining, and already 120 minutes running). I try to see if this setup is getting any better.

---

