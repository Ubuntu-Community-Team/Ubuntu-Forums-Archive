---
title: "RAID5 Errors in mdadm"
date: 2013-10-28
forum: Server Platforms
---

### Post by mattem on 2013-10-28
The other night I received an error from our server saying that one of the drives in the raid had failed. As I am quite new to using mdadm and Ubuntu server I use Webmin to help add the drive back in to the raid array. At first, it seemed to be rebuilding the array and I could still access the data. However, during this process the status changed and now displays:

```

RAID errors    2 disks have failed
RAID status    clean, FAILED
Partitions in RAID    SATA device C partition 1 (Down) 
SATA device D partition 1 
Spare partitions    SATA device B partition 1

```

When trying to access the data, the output gives:
```
matt@sancho:/mnt/raid5/superstore/Pictures$ ls
ls: reading directory .: Input/output error

```

The drive that I originally tried to re-add to the array is now listed under 'Spare Partitions'. 
I've read some forum posts but a little lost on how to continue.

The output of mdadm --examine /dev/sd[bcd]1 | less shows:

```
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : abf2d149:17b898a5:dc729097:dc568827
           Name : sancho:0  (local to host sancho)
  Creation Time : Mon Apr 22 19:50:07 2013
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
     Array Size : 1953259248 (1862.77 GiB 2000.14 GB)
  Used Dev Size : 1953259248 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 0c211973:550b078d:75763389:edab3bb7


    Update Time : Mon Oct 28 19:55:01 2013
       Checksum : b86bf8cd - correct
         Events : 2488


         Layout : left-symmetric
     Chunk Size : 4K


   Device Role : spare
   Array State : ..A ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : abf2d149:17b898a5:dc729097:dc568827
           Name : sancho:0  (local to host sancho)
  Creation Time : Mon Apr 22 19:50:07 2013
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
     Array Size : 1953259248 (1862.77 GiB 2000.14 GB)
  Used Dev Size : 1953259248 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 8936a688:41b411d4:91c5e733:9e22f2db


    Update Time : Mon Oct 28 19:08:32 2013
       Checksum : e47071e7 - correct
         Events : 2436


         Layout : left-symmetric
     Chunk Size : 4K


   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : abf2d149:17b898a5:dc729097:dc568827
          Name : sancho:0  (local to host sancho)
  Creation Time : Mon Apr 22 19:50:07 2013
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 1953259520 (931.39 GiB 1000.07 GB)
     Array Size : 1953259248 (1862.77 GiB 2000.14 GB)
  Used Dev Size : 1953259248 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 0f85443e:4ba98525:51acb633:9fc74909


    Update Time : Mon Oct 28 19:55:01 2013
       Checksum : 18a7471a - correct
         Events : 2488


         Layout : left-symmetric
     Chunk Size : 4K


   Device Role : Active device 2
   Array State : ..A ('A' == active, '.' == missing)


```

Any help would be greatly appreciated.

---

### Post by SaturnusDJ on 2013-10-28
Begin with looking into the SMART data of all the disks...because we need to know what went wrong.
```

smartctl -a /dev/sda
smartctl -a /dev/sdb
smartctl -a /dev/sdc
smartctl -a /dev/sdd

```

Then, if that looks fine (post here to verify), try to assemble it.
First stop all running md devices containing members of this array.

If you need help on that I'll need the output of
```

cat /proc/mdstat

```

Then assemble:
```

mdadm --assemble /dev/md0 --uuid=abf2d149:17b898a5:dc729097:dc568827

```

If this fails, you can try with the --force and --run flag, like so:
```

mdadm --assemble --force --run /dev/md0 --uuid=abf2d149:17b898a5:dc729097:dc568827

```

Now hopefully the rebuilding will continue.

---

### Post by mattem on 2013-10-28
Thanks for your reply, below is output of the commands:
smartctrl -a /dev/sda
(This is the SSD the system is on)
```
=== START OF INFORMATION SECTION ===Device Model:     Corsair Nova 2 SSD
Serial Number:    13096500000013450344
LU WWN Device Id: 0 000000 000000000
Firmware Version: 5.05
User Capacity:    30,016,659,456 bytes [30.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ACS-2 revision 3
Local Time is:    Mon Oct 28 21:18:44 2013 GMT
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
data collection:                (    0) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  48) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x0021) SCT Status supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   120   120   050    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0033   100   100   003    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4621 (170 106 0)
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       14
171 Unknown_Attribute       0x0032   000   000   000    Old_age   Always       -       0
172 Unknown_Attribute       0x0032   000   000   000    Old_age   Always       -       0
174 Unknown_Attribute       0x0030   000   000   000    Old_age   Offline      -       10
177 Wear_Leveling_Count     0x0000   000   000   000    Old_age   Offline      -       1
181 Program_Fail_Cnt_Total  0x0032   000   000   000    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   000   000   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0022   030   030   000    Old_age   Always       -       30 (Min/Max 30/30)
195 Hardware_ECC_Recovered  0x001c   100   100   000    Old_age   Offline      -       0
196 Reallocated_Event_Count 0x0033   100   100   003    Pre-fail  Always       -       0
201 Soft_Read_Error_Rate    0x001c   100   100   000    Old_age   Offline      -       0
204 Soft_ECC_Correction     0x001c   100   100   000    Old_age   Offline      -       0
230 Head_Amplitude          0x0013   100   100   000    Pre-fail  Always       -       100
231 Temperature_Celsius     0x0013   100   100   010    Pre-fail  Always       -       0
233 Media_Wearout_Indicator 0x0000   000   000   000    Old_age   Offline      -       625
234 Unknown_Attribute       0x0032   000   000   000    Old_age   Always       -       375
241 Total_LBAs_Written      0x0032   000   000   000    Old_age   Always       -       375
242 Total_LBAs_Read         0x0032   000   000   000    Old_age   Always       -       70


SMART Error Log not supported
SMART Self-test Log not supported
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


```

smartctrl -a /dev/sdb
```

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda LP
Device Model:     ST31000520AS
Serial Number:    9VX05EKM
LU WWN Device Id: 5 000c50 0159f3fb2
Firmware Version: CC32
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Mon Oct 28 21:22:07 2013 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (  633) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 225) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   100   006    Pre-fail  Always       -       232395993
  3 Spin_Up_Time            0x0003   096   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       131
  5 Reallocated_Sector_Ct   0x0033   095   095   036    Pre-fail  Always       -       228
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       347909
  9 Power_On_Hours          0x0032   077   077   000    Old_age   Always       -       20593
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       41
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   049   049   000    Old_age   Always       -       51
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       38655295497
189 High_Fly_Writes         0x003a   001   001   000    Old_age   Always       -       217
190 Airflow_Temperature_Cel 0x0022   073   055   045    Old_age   Always       -       27 (Min/Max 26/27)
194 Temperature_Celsius     0x0022   027   045   000    Old_age   Always       -       27 (0 15 0 0 0)
195 Hardware_ECC_Recovered  0x001a   044   023   000    Old_age   Always       -       232395993
197 Current_Pending_Sector  0x0012   098   098   000    Old_age   Always       -       87
198 Offline_Uncorrectable   0x0010   098   098   000    Old_age   Offline      -       87
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       244491013330938
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       532656861
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3826133161


SMART Error Log Version: 1
ATA Error Count: 51 (device log contains only the most recent five errors)
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 51 occurred at disk power-on lifetime: 20574 hours (857 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00  29d+22:37:42.205  READ DMA EXT
  35 00 10 ff ff ff ef 00  29d+22:37:42.204  WRITE DMA EXT
  ea 00 00 00 00 00 a0 00  29d+22:37:42.171  FLUSH CACHE EXT
  ca 00 01 08 08 00 e0 00  29d+22:37:42.170  WRITE DMA
  ea 00 00 00 00 00 a0 00  29d+22:37:42.170  FLUSH CACHE EXT


Error 50 occurred at disk power-on lifetime: 20574 hours (857 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00  29d+22:19:06.639  READ DMA EXT
  35 00 48 ff ff ff ef 00  29d+22:19:06.637  WRITE DMA EXT
  35 00 70 ff ff ff ef 00  29d+22:19:06.636  WRITE DMA EXT
  35 00 78 ff ff ff ef 00  29d+22:19:06.635  WRITE DMA EXT
  35 00 70 ff ff ff ef 00  29d+22:19:06.634  WRITE DMA EXT


Error 49 occurred at disk power-on lifetime: 20574 hours (857 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00  29d+22:16:18.618  READ DMA EXT
  35 00 08 ff ff ff ef 00  29d+22:16:18.617  WRITE DMA EXT
  35 00 40 ff ff ff ef 00  29d+22:16:18.616  WRITE DMA EXT
  35 00 78 ff ff ff ef 00  29d+22:16:18.615  WRITE DMA EXT
  35 00 70 ff ff ff ef 00  29d+22:16:18.614  WRITE DMA EXT
Error 48 occurred at disk power-on lifetime: 20573 hours (857 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00  29d+22:12:41.601  READ DMA EXT
  35 00 08 ff ff ff ef 00  29d+22:12:41.600  WRITE DMA EXT
  35 00 48 ff ff ff ef 00  29d+22:12:41.599  WRITE DMA EXT
  35 00 70 ff ff ff ef 00  29d+22:12:41.598  WRITE DMA EXT
  35 00 78 ff ff ff ef 00  29d+22:12:41.597  WRITE DMA EXT


Error 47 occurred at disk power-on lifetime: 20573 hours (857 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00  29d+22:09:18.304  READ DMA EXT
  25 00 08 ff ff ff ef 00  29d+22:09:18.250  READ DMA EXT
  35 00 08 ff ff ff ef 00  29d+22:09:18.234  WRITE DMA EXT
  35 00 08 ff ff ff ef 00  29d+22:09:18.234  WRITE DMA EXT
  35 00 08 ff ff ff ef 00  29d+22:09:18.233  WRITE DMA EXT


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





```

smartctrl -a /dev/sdc
```

Model Family:     Seagate Barracuda 7200.12
Device Model:     ST31000528AS
Serial Number:    5VP5G1Z8
LU WWN Device Id: 5 000c50 027f6b5e1
Firmware Version: CC46
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Mon Oct 28 21:24:19 2013 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.


General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (  609) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 171) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   108   100   006    Pre-fail  Always       -       135112704
  3 Spin_Up_Time            0x0003   095   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       308
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       11
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       278690
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4950
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       92
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   093   093   000    Old_age   Always       -       7
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       393222
189 High_Fly_Writes         0x003a   099   099   000    Old_age   Always       -       1
190 Airflow_Temperature_Cel 0x0022   073   045   045    Old_age   Always   In_the_past 27 (Min/Max 27/27)
194 Temperature_Celsius     0x0022   027   055   000    Old_age   Always       -       27 (0 14 0 0 0)
195 Hardware_ECC_Recovered  0x001a   035   023   000    Old_age   Always       -       135112704
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       1
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       164514427306238
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       4281370016
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3962290274


SMART Error Log Version: 1
ATA Error Count: 8 (device log contains only the most recent five errors)
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   108   100   006    Pre-fail  Always       -       135112704
  3 Spin_Up_Time            0x0003   095   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       308
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       11
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       278690
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4950
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       92
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   093   093   000    Old_age   Always       -       7
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       393222
189 High_Fly_Writes         0x003a   099   099   000    Old_age   Always       -       1
190 Airflow_Temperature_Cel 0x0022   073   045   045    Old_age   Always   In_the_past 27 (Min/Max 27/27)
194 Temperature_Celsius     0x0022   027   055   000    Old_age   Always       -       27 (0 14 0 0 0)
195 Hardware_ECC_Recovered  0x001a   035   023   000    Old_age   Always       -       135112704
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       1
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       164514427306238
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       4281370016
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3962290274


Error 8 occurred at disk power-on lifetime: 4947 hours (206 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 42 d3 cf 01  Error: UNC at LBA = 0x01cfd342 = 30397250


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 48 d6 cf 41 00      00:21:28.588  READ FPDMA QUEUED
  60 00 00 48 d2 cf 41 00      00:21:28.587  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00      00:21:28.587  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:21:28.586  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:21:28.586  SET FEATURES [Set transfer mode]


Error 7 occurred at disk power-on lifetime: 4947 hours (206 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 42 d3 cf 01  Error: UNC at LBA = 0x01cfd342 = 30397250


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 00 cc cc 41 00      00:21:11.516  READ FPDMA QUEUED
  60 00 00 00 c8 cc 41 00      00:21:11.516  READ FPDMA QUEUED
  60 00 08 08 08 00 40 00      00:21:10.736  READ FPDMA QUEUED
  60 00 08 00 08 00 40 00      00:21:10.736  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:21:10.736  READ FPDMA QUEUED


Error 6 occurred at disk power-on lifetime: 2917 hours (121 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 41 d3 cf 01  Error: UNC at LBA = 0x01cfd341 = 30397249


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 c8 d8 cf 41 00   5d+00:24:36.153  READ FPDMA QUEUED
  60 00 00 c8 d0 cf 41 00   5d+00:24:36.120  READ FPDMA QUEUED
  60 00 00 c8 d4 cf 41 00   5d+00:24:36.119  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00   5d+00:24:36.119  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00   5d+00:24:36.117  IDENTIFY DEVICE


Error 5 occurred at disk power-on lifetime: 2917 hours (121 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 41 d3 cf 01  Error: UNC at LBA = 0x01cfd341 = 30397249


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 c8 84 c1 41 00   5d+00:24:19.571  READ FPDMA QUEUED
  60 00 00 c8 80 c1 41 00   5d+00:24:19.555  READ FPDMA QUEUED
  60 00 00 c8 7c c1 41 00   5d+00:24:19.535  READ FPDMA QUEUED
  60 00 00 c8 78 c1 41 00   5d+00:24:19.535  READ FPDMA QUEUED
  ea 00 00 00 00 00 a0 00   5d+00:24:19.504  FLUSH CACHE EXT


Error 4 occurred at disk power-on lifetime: 2245 hours (93 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 42 d3 cf 01  Error: UNC at LBA = 0x01cfd342 = 30397250


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 30 d8 cf 41 00  26d+17:25:15.717  READ FPDMA QUEUED
  60 00 00 30 d0 cf 41 00  26d+17:25:15.700  READ FPDMA QUEUED
  60 00 00 30 d4 cf 41 00  26d+17:25:15.699  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00  26d+17:25:15.699  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00  26d+17:25:15.698  IDENTIFY DEVICE


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






```

smartctrl -a /dev/sdd
```

Model Family:     SAMSUNG SpinPoint F2 EG
Device Model:     SAMSUNG HD103SI
Serial Number:    S1VSJ9BSB02161
LU WWN Device Id: 5 0024e9 20153cef7
Firmware Version: 1AG01118
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3b
Local Time is:    Mon Oct 28 21:26:55 2013 GMT
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
data collection:                (13071) seconds.
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
recommended polling time:        ( 219) minutes.
Conveyance self-test routine
recommended polling time:        (  23) minutes.
SCT capabilities:              (0x003f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   082   082   011    Pre-fail  Always       -       6230
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2379
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       10572
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       3
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       463
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       1
184 End-to-End_Error        0x0033   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   079   062   000    Old_age   Always       -       21 (Min/Max 21/21)
194 Temperature_Celsius     0x0022   079   060   000    Old_age   Always       -       21 (Min/Max 21/22)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       5144164
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       1
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0


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


```

There does seem quite a few 'errors' here.

Output of cat /proc/mdstat gives
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] md0 : active raid5 sdb1[4](S) sdd1[3] sdc1[1](F)
      1953259248 blocks super 1.2 level 5, 4k chunk, algorithm 2 [3/1] [__U]
      
unused devices: <none>
```

---

### Post by SaturnusDJ on 2013-10-28
/dev/sdb and /dev/sdc look totally destroyed.

Things are not looking good.

Let's do some tests.
```

smartctl -t short /dev/sdb
smartctl -t short /dev/sdc

```

After this post the results:
```

smartctl -a /dev/sdb
smartctl -a /dev/sdc

```

---

### Post by mattem on 2013-10-28
Output from smartctrl -a /dev/sdb

```
=== START OF INFORMATION SECTION ===Model Family:     Seagate Barracuda LP
Device Model:     ST31000520AS
Serial Number:    9VX05EKM
LU WWN Device Id: 5 000c50 0159f3fb2
Firmware Version: CC32
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Mon Oct 28 22:22:01 2013 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121) The previous self-test completed having
                                        the read element of the test failed.
Total time to complete Offline 
data collection:                (  633) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 225) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   100   006    Pre-fail  Always       -       232395993
  3 Spin_Up_Time            0x0003   096   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       131
  5 Reallocated_Sector_Ct   0x0033   095   095   036    Pre-fail  Always       -       228
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       348010
  9 Power_On_Hours          0x0032   077   077   000    Old_age   Always       -       20594
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       41
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   049   049   000    Old_age   Always       -       51
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       38655295497
189 High_Fly_Writes         0x003a   001   001   000    Old_age   Always       -       217
190 Airflow_Temperature_Cel 0x0022   074   055   045    Old_age   Always       -       26 (Min/Max 26/27)
194 Temperature_Celsius     0x0022   026   045   000    Old_age   Always       -       26 (0 15 0 0 0)
195 Hardware_ECC_Recovered  0x001a   043   023   000    Old_age   Always       -       232395993
197 Current_Pending_Sector  0x0012   098   098   000    Old_age   Always       -       88
198 Offline_Uncorrectable   0x0010   098   098   000    Old_age   Offline      -       88
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       217913755703291
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       532656885
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3826133161


SMART Error Log Version: 1
ATA Error Count: 51 (device log contains only the most recent five errors)
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.
Error 51 occurred at disk power-on lifetime: 20574 hours (857 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00  29d+22:37:42.205  READ DMA EXT
  35 00 10 ff ff ff ef 00  29d+22:37:42.204  WRITE DMA EXT
  ea 00 00 00 00 00 a0 00  29d+22:37:42.171  FLUSH CACHE EXT
  ca 00 01 08 08 00 e0 00  29d+22:37:42.170  WRITE DMA
  ea 00 00 00 00 00 a0 00  29d+22:37:42.170  FLUSH CACHE EXT


Error 50 occurred at disk power-on lifetime: 20574 hours (857 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00  29d+22:19:06.639  READ DMA EXT
  35 00 48 ff ff ff ef 00  29d+22:19:06.637  WRITE DMA EXT
  35 00 70 ff ff ff ef 00  29d+22:19:06.636  WRITE DMA EXT
  35 00 78 ff ff ff ef 00  29d+22:19:06.635  WRITE DMA EXT
  35 00 70 ff ff ff ef 00  29d+22:19:06.634  WRITE DMA EXT


Error 49 occurred at disk power-on lifetime: 20574 hours (857 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00  29d+22:16:18.618  READ DMA EXT
  35 00 08 ff ff ff ef 00  29d+22:16:18.617  WRITE DMA EXT
  35 00 40 ff ff ff ef 00  29d+22:16:18.616  WRITE DMA EXT
  35 00 78 ff ff ff ef 00  29d+22:16:18.615  WRITE DMA EXT
  35 00 70 ff ff ff ef 00  29d+22:16:18.614  WRITE DMA EXT
Error 48 occurred at disk power-on lifetime: 20573 hours (857 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00  29d+22:12:41.601  READ DMA EXT
  35 00 08 ff ff ff ef 00  29d+22:12:41.600  WRITE DMA EXT
  35 00 48 ff ff ff ef 00  29d+22:12:41.599  WRITE DMA EXT
  35 00 70 ff ff ff ef 00  29d+22:12:41.598  WRITE DMA EXT
  35 00 78 ff ff ff ef 00  29d+22:12:41.597  WRITE DMA EXT


Error 47 occurred at disk power-on lifetime: 20573 hours (857 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00  29d+22:09:18.304  READ DMA EXT
  25 00 08 ff ff ff ef 00  29d+22:09:18.250  READ DMA EXT
  35 00 08 ff ff ff ef 00  29d+22:09:18.234  WRITE DMA EXT
  35 00 08 ff ff ff ef 00  29d+22:09:18.234  WRITE DMA EXT
  35 00 08 ff ff ff ef 00  29d+22:09:18.233  WRITE DMA EXT


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%     20594         1406744400


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




```

Output of smartctl -a /dev/sdc
```

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.12
Device Model:     ST31000528AS
Serial Number:    5VP5G1Z8
LU WWN Device Id: 5 000c50 027f6b5e1
Firmware Version: CC46
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Mon Oct 28 22:24:30 2013 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.


General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121) The previous self-test completed having
                                        the read element of the test failed.
Total time to complete Offline 
data collection:                (  609) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 171) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   108   100   006    Pre-fail  Always       -       135112704
  3 Spin_Up_Time            0x0003   095   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       308
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       11
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       278793
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4951
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       92
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   093   093   000    Old_age   Always       -       7
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       393222
189 High_Fly_Writes         0x003a   099   099   000    Old_age   Always       -       1
190 Airflow_Temperature_Cel 0x0022   073   045   045    Old_age   Always   In_the_past 27 (Min/Max 27/27)
194 Temperature_Celsius     0x0022   027   055   000    Old_age   Always       -       27 (0 14 0 0 0)
195 Hardware_ECC_Recovered  0x001a   034   023   000    Old_age   Always       -       135112704
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       1
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       210071145414911
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       4281370016
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3962290274


SMART Error Log Version: 1
ATA Error Count: 8 (device log contains only the most recent five errors)
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.
Error 8 occurred at disk power-on lifetime: 4947 hours (206 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 42 d3 cf 01  Error: UNC at LBA = 0x01cfd342 = 30397250


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 48 d6 cf 41 00      00:21:28.588  READ FPDMA QUEUED
  60 00 00 48 d2 cf 41 00      00:21:28.587  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00      00:21:28.587  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:21:28.586  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:21:28.586  SET FEATURES [Set transfer mode]


Error 7 occurred at disk power-on lifetime: 4947 hours (206 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 42 d3 cf 01  Error: UNC at LBA = 0x01cfd342 = 30397250


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 00 cc cc 41 00      00:21:11.516  READ FPDMA QUEUED
  60 00 00 00 c8 cc 41 00      00:21:11.516  READ FPDMA QUEUED
  60 00 08 08 08 00 40 00      00:21:10.736  READ FPDMA QUEUED
  60 00 08 00 08 00 40 00      00:21:10.736  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:21:10.736  READ FPDMA QUEUED


Error 6 occurred at disk power-on lifetime: 2917 hours (121 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 41 d3 cf 01  Error: UNC at LBA = 0x01cfd341 = 30397249


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 c8 d8 cf 41 00   5d+00:24:36.153  READ FPDMA QUEUED
  60 00 00 c8 d0 cf 41 00   5d+00:24:36.120  READ FPDMA QUEUED
  60 00 00 c8 d4 cf 41 00   5d+00:24:36.119  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00   5d+00:24:36.119  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00   5d+00:24:36.117  IDENTIFY DEVICE
Error 5 occurred at disk power-on lifetime: 2917 hours (121 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 41 d3 cf 01  Error: UNC at LBA = 0x01cfd341 = 30397249


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 c8 84 c1 41 00   5d+00:24:19.571  READ FPDMA QUEUED
  60 00 00 c8 80 c1 41 00   5d+00:24:19.555  READ FPDMA QUEUED
  60 00 00 c8 7c c1 41 00   5d+00:24:19.535  READ FPDMA QUEUED
  60 00 00 c8 78 c1 41 00   5d+00:24:19.535  READ FPDMA QUEUED
  ea 00 00 00 00 00 a0 00   5d+00:24:19.504  FLUSH CACHE EXT


Error 4 occurred at disk power-on lifetime: 2245 hours (93 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 42 d3 cf 01  Error: UNC at LBA = 0x01cfd342 = 30397250


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 30 d8 cf 41 00  26d+17:25:15.717  READ FPDMA QUEUED
  60 00 00 30 d0 cf 41 00  26d+17:25:15.700  READ FPDMA QUEUED
  60 00 00 30 d4 cf 41 00  26d+17:25:15.699  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00  26d+17:25:15.699  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00  26d+17:25:15.698  IDENTIFY DEVICE


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      4950         30397250


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




```

If they are gone, then it's not the end of the world, just means we have to rip the blu-ray collection again!

---

### Post by SaturnusDJ on 2013-10-28
You can try to continue with the commands from my first post, and see what happens, but if the S.M.A.R.T. data is true, it won't hold out long.

Before assembling stop the running array first.
```

mdadm --stop /dev/md0

```


After you bought new hard disks, setup regular checks for S.M.A.R.T. so you can see this coming.
[http://zackreed.me/articles/45-how-do-i-know-if-my-hard-drive-is-failing](http://zackreed.me/articles/45-how-do-i-know-if-my-hard-drive-is-failing)

---

### Post by mattem on 2013-10-28
Okay - I guess that may be enough to get the data off the array and get some new drives. 
I had to run with the --force option, do I add the partitions back to the array now? As it shows that the array is now inactive. 

```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[3](S) sdb1[4](S) sdc1[1](S)
      2929889280 blocks super 1.2
       
unused devices: <none>

```

---

### Post by SaturnusDJ on 2013-10-28
Then it didn't work. Maybe it won't force when using uuid.

Try this:
```

mdadm --stop /dev/md0
mdadm --assemble --force --run /dev/md0 /dev/sd[b-d]1

```

Now I gotta sleep. :P
Back in 12 hours.

---

### Post by rubylaser on 2013-10-28
I would try to assemble the array without /dev/sdb1, because it's obviously not good (the uncorrectable errors increased even during a short SMART test). /dev/sdc doesn't look fantastic, but it only has one uncorrectable error, so it's likely that it can still be used.

```

sudo -i
mdadm --stop /dev/md0
mdadm --assemble --force --run /dev/md0 /dev/sd[cd]1

```

Without the force flag at this point, any efforts to assemble the array will likely fail.

Before doing that, it would be nice to see the event counters on those two disks to make sure they are similar.
```

mdadm -E /dev/sd[cd]1

```

Also, if all hope seems lost, you always have the option try to gddrescue the best of the failed disks to a new disk and try to assemble with that.  Please let us know the output of the mdadm -E before proceeding.

---

### Post by SaturnusDJ on 2013-10-29
More must have happened to /dev/sdb. 'Total_LBAs_Written' changed also.

Looking at the first post, /dev/sdc1 and /dev/sdd1 differ by 52 events. Not ideal, but could have been worse too.

---

