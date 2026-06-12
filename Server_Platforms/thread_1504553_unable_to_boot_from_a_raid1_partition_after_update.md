---
title: "unable to boot from a raid1 partition after update from 9.04 to 10.04"
date: 2010-06-08
forum: Server Platforms
---

### Post by bjelakrez on 2010-06-08
a little backstory:
I have a ubuntu server that has been running for more than 3 years without a problem. i didn't update it for a year because i reckoned 'if it ain't broke, don't fix it'. well, yesterday i gave up and went for an update. i did a release upgrade and after the reboot it didn't boot. it's a headless server so i then had to put the graphics card in and plug in the monitor, keyboard and all that. when i booted it again i saw that it put me in busybox. after a lot of wasted hours i managed to figure out that i can boot it (although not without problems) using an older kernel (2.6.27-7-server). so now it's sort of running...i'm not satisfied (as you'd imagine). the essential thing to mention is that my root partition is on a raid1 (/dev/md0) array.

i really hope that someone will try to answer *ANY* of the following questions.

my questions are (sorry if they're n00b questions, i hope someone will be so kind as to help me):
[LIST=1]
[*]how can i edit files that 'belong' to other kernels?
[INDENT]i end up in busybox regardless of which kernel i use. the thing is that when i use 2.6.27-7-server i can then run ```
mdadm --assemble --scan
``` and it assembles /dev/md0. i then just exit and it continues to boot fine. if i use the latest kernel (2.6.32-22-generic-pae) or any kernel that is newer than 2.6.27-7-server that command doesn't work. i think the problem is that if i run ```
cat /etc/mdadm/mdadm.conf
``` in busybox when using the latest kernel, the file is different than if i check mdadm.conf when using 2.6.27-7-server. the uuids of the arrays are different. i should mention that i changed the mdadm.conf that 2.6.32-22-generic-pae uses when trying to solve my problems, i just don't know how i can change it back. so: how can i change the file /etc/mdadm/mdadm.conf that 2.6.32-22-generic-pae uses so that i could boot using the newest kernel?[/INDENT]

[*]in busybox i noticed that in 2.6.32-22-generic-pae module md_mod wasn't loaded, while in 2.6.27-7-server it was. is this a problem? if yes, how can i make sure it's loaded when using 2.6.32-22-generic-pae?

[*]why all of a sudden the newer kernels are not 'server' anymore, but 'generic' instead? did i do something wrong when upgrading? should the newer kernels also be 'server'? 

[*]what does that 'pae' mean in the latest kernel?

[*]is one of my hard drives failing?
[INDENT]before i'm dropped into busybox, i get these errors: ```
[    6.812229] ata5.00: status: { DRDY ERR }
[    6.812288] ata5.00: error: { ICRC ABRT }
``` is this something to worry about? is this the reason why /dev/md0 doesn't assemble on itself? that hard drive is part of the /dev/md0 array. why does it still assemble if i do it manually from busybox? this is the output of sudo smartctl --all /dev/sde:```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint T133 series
Device Model:     SAMSUNG HD400LD
Serial Number:    S0AXJDWPA04087
Firmware Version: WQ100-15
User Capacity:    400,087,375,360 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 4a
Local Time is:    Tue Jun  8 11:23:00 2010 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x05) Offline data collection activity
                                        was aborted by an interrupting command from host.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                 (7607) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 129) minutes.
SCT capabilities:              (0x003f) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   100   100   015    Pre-fail  Always       -       7744
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       18
  5 Reallocated_Sector_Ct   0x0033   253   253   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   253   253   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       13870
 10 Spin_Retry_Count        0x0033   253   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   253   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       11
190 Airflow_Temperature_Cel 0x0022   057   054   000    Old_age   Always       -       43
194 Temperature_Celsius     0x0022   109   100   000    Old_age   Always       -       43
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       1443128
196 Reallocated_Event_Count 0x0032   253   253   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   253   253   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 214 (device log contains only the most recent five errors)
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

Error 214 occurred at disk power-on lifetime: 13869 hours (577 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 08 00 00 00 e0  Error: ICRC, ABRT 8 sectors at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 00 00 e0 00      16:14:51.500  READ DMA
  ec 00 00 00 00 00 a0 00      16:14:51.500  IDENTIFY DEVICE
  ef 03 44 00 00 00 a0 00      16:14:51.500  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      16:14:51.500  IDENTIFY DEVICE
  00 00 01 01 00 00 a0 00      16:14:51.313  NOP [Abort queued commands]

Error 213 occurred at disk power-on lifetime: 13869 hours (577 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 08 00 00 00 e0  Error: ICRC, ABRT 8 sectors at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 00 00 e0 00      16:14:51.250  READ DMA
  ec 00 00 00 00 00 a0 00      16:14:51.250  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      16:14:51.250  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      16:14:51.188  IDENTIFY DEVICE
  00 00 01 01 00 00 a0 00      16:14:51.063  NOP [Abort queued commands]

Error 212 occurred at disk power-on lifetime: 13869 hours (577 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 08 00 00 00 e0  Error: ICRC, ABRT 8 sectors at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 00 00 e0 00      16:14:51.000  READ DMA
  ec 00 00 00 00 00 a0 00      16:14:50.750  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      16:14:50.750  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      16:14:50.688  IDENTIFY DEVICE
  00 00 01 01 00 00 a0 00      16:14:50.563  NOP [Abort queued commands]

Error 211 occurred at disk power-on lifetime: 13869 hours (577 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 08 00 00 00 e0  Error: ICRC, ABRT 8 sectors at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 00 00 e0 00      16:11:24.500  READ DMA
  ec 00 00 00 00 00 a0 00      16:11:24.500  IDENTIFY DEVICE
  ef 03 44 00 00 00 a0 00      16:11:24.500  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      16:11:24.500  IDENTIFY DEVICE
  00 00 01 01 00 00 a0 00      16:11:24.375  NOP [Abort queued commands]

Error 210 occurred at disk power-on lifetime: 13869 hours (577 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 08 00 00 00 e0  Error: ICRC, ABRT 8 sectors at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 00 00 e0 00      16:11:24.313  READ DMA
  ec 00 00 00 00 00 a0 00      16:11:24.250  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      16:11:24.250  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      16:11:24.250  IDENTIFY DEVICE
  00 00 01 01 00 00 a0 00      16:11:24.125  NOP [Abort queued commands]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     13866         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
``` can anyone tell me what's happening with this hdd?[/INDENT]
[/LIST]

can anyone help me with any of my problems? thank you in advance!

---

### Post by benderisgreat on 2010-06-08
there is only one /etc/mdadm/mdadm.conf, different kernels don't use different files. 

you need to update your initramfs after you edit mdadm.conf with the correct uuid.

you do need the md_mod module. it appears the initrd for the new kernel wasn't built with that module. try this:

```
echo "md_mod" >> /etc/initramfs-tools/modules
```
and then run
```
update-initramfs -u -k 2.6.32-22-generic-pae
```
and see if it boots

you can change back to a server kernel later.
pae stands for physical address extensions which allow you to use more than 4G of ram with a 32bit kernel.

---

### Post by bjelakrez on 2010-06-08
amazing! it booted! thank you for helping me. i'm not really at home with initramfs. thank you for clearing up a lot of things for me.

why wasn't md_mod module included by default in the new kernels? i assume it was in the previous, since this step wasn't necessary. 

how can i switch to server kernel? why would i want to use the generic one and/or why would it be better to continue using the server one? which one is 'better'?

do you (or anyone else) know anything about those HDD-related errors and the hdd failing?

thanks

---

### Post by bjelakrez on 2010-06-16
i replaced the IDE cable and it seems the HDD errors on boot are gone.

---

