---
title: "Kernel Patch or Upgrade to save Hard Drive: Which one or how to?"
date: 2016-03-01
forum: Ubuntu Studio
---

### Post by marseille2 on 2016-03-01
I've had an [on-going HD problem]("http://ubuntuforums.org/showthread.php?t=2267746") -- on Trusty LTS -- since about March 2015 that seems to be kernel related ... at least that's what I gather from Bugzilla's [Bug 93581]("https://bugzilla.kernel.org/show_bug.cgi?id=93581"). The HD itself seems fine according to smartctl.


Output of HD check:

```
$  sudo smartctl -a -d ata /dev/sda


smartctl 6.2 2013-07-26 r3841 [x86_64-linux-4.2.0-30-lowlatency] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.14 (AF)
Device Model:     ST500DM002-1BD142
Serial Number:    Z6EBBMNP
LU WWN Device Id: 5 000c50 0794e400c
Firmware Version: KC48
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 1.5 Gb/s)
Local Time is:    Tue Mar  1 08:20:35 2016 PST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  600) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  86) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   107   099   006    Pre-fail  Always       -       643200
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   093   093   020    Old_age   Always       -       7672
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   061   060   030    Pre-fail  Always       -       1313847
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       7758
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       209
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   098   098   000    Old_age   Always       -       2
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0 0 2
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   062   061   045    Old_age   Always       -       38 (Min/Max 38/39)
194 Temperature_Celsius     0x0022   038   040   000    Old_age   Always       -       38 (0 21 0 0 0)
195 Hardware_ECC_Recovered  0x001a   053   040   000    Old_age   Always       -       643200
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       84h+24m+17.955s
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       1842753940
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2538679405


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       147         -
# 2  Short offline       Completed without error       00%       146         -


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


But this is what my kern log keeps spitting out, which is similar to other bug [reports]("https://bugzilla.kernel.org/show_bug.cgi?id=93581"), as well as the one I [posted]("http://ubuntuforums.org/showthread.php?t=2267746") a year ago and thought was "solved."

```
Feb 28 07:57:51 av kernel: [255237.333293] ata3.00: exception Emask 0x10 SAct 0x2000 SErr 0x10200 ac
tion 0xe frozen
Feb 28 07:57:51 av kernel: [255237.333300] ata3.00: irq_stat 0x00400000, PHY RDY changed
Feb 28 07:57:51 av kernel: [255237.333305] ata3: SError: { Persist PHYRdyChg }
Feb 28 07:57:51 av kernel: [255237.333311] ata3.00: failed command: READ FPDMA QUEUED
Feb 28 07:57:51 av kernel: [255237.333319] ata3.00: cmd 60/08:68:a0:67:41/00:00:02:00:00/40 tag 13 n
cq 4096 in
Feb 28 07:57:51 av kernel: [255237.333319]          res 40/00:68:a0:67:41/00:00:02:00:00/40 Emask 0x
10 (ATA bus error)
Feb 28 07:57:51 av kernel: [255237.333324] ata3.00: status: { DRDY }
Feb 28 07:57:51 av kernel: [255237.333330] ata3: hard resetting link
Feb 28 07:57:55 av kernel: [255240.971739] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 28 07:57:55 av kernel: [255240.974710] ata3.00: configured for UDMA/33
Feb 28 07:57:55 av kernel: [255240.985643] ata3: EH complete
Feb 28 07:57:55 av kernel: [255241.198144] ata3.00: exception Emask 0x10 SAct 0x1ff80000 SErr 0x40d0
202 action 0xe frozen
Feb 28 07:57:55 av kernel: [255241.198152] ata3.00: irq_stat 0x00000040, connection status changed
Feb 28 07:57:55 av kernel: [255241.198158] ata3: SError: { RecovComm Persist PHYRdyChg CommWake 10B8
B DevExch }
Feb 28 07:57:55 av kernel: [255241.198164] ata3.00: failed command: READ FPDMA QUEUED
Feb 28 07:57:55 av kernel: [255241.198173] ata3.00: cmd 60/08:98:80:3d:01/00:00:02:00:00/40 tag 19 n
cq 4096 in
Feb 28 07:57:55 av kernel: [255241.198173]          res 40/00:e0:58:1e:dc/00:00:01:00:00/40 Emask 0x
10 (ATA bus error)
Feb 28 07:57:55 av kernel: [255241.198178] ata3.00: status: { DRDY }
Feb 28 07:57:55 av kernel: [255241.198183] ata3.00: failed command: WRITE FPDMA QUEUED
Feb 28 07:57:55 av kernel: [255241.198190] ata3.00: cmd 61/40:a0:c8:b8:ef/05:00:06:00:00/40 tag 20 n
cq 688128 out
Feb 28 07:57:55 av kernel: [255241.198190]          res 40/00:e0:58:1e:dc/00:00:01:00:00/40 Emask 0x
10 (ATA bus error)
Feb 28 07:57:55 av kernel: [255241.198195] ata3.00: status: { DRDY }
Feb 28 07:57:55 av kernel: [255241.198198] ata3.00: failed command: WRITE FPDMA QUEUED
Feb 28 07:57:55 av kernel: [255241.198206] ata3.00: cmd 61/40:a8:08:be:ef/05:00:06:00:00/40 tag 21 n
cq 688128 out
Feb 28 07:57:55 av kernel: [255241.198206]          res 40/00:e0:58:1e:dc/00:00:01:00:00/40 Emask 0x
10 (ATA bus error)
Feb 28 07:57:55 av kernel: [255241.198210] ata3.00: status: { DRDY }
Feb 28 07:57:55 av kernel: [255241.198213] ata3.00: failed command: WRITE FPDMA QUEUED
Feb 28 07:57:55 av kernel: [255241.198220] ata3.00: cmd 61/40:b0:48:c3:ef/05:00:06:00:00/40 tag 22 n
cq 688128 out
Feb 28 07:57:55 av kernel: [255241.198220]          res 40/00:e0:58:1e:dc/00:00:01:00:00/40 Emask 0x
10 (ATA bus error)
Feb 28 07:57:55 av kernel: [255241.198224] ata3.00: status: { DRDY }
Feb 28 07:57:55 av kernel: [255241.198228] ata3.00: failed command: WRITE FPDMA QUEUED
Feb 28 07:57:55 av kernel: [255241.198235] ata3.00: cmd 61/40:b8:88:c8:ef/05:00:06:00:00/40 tag 23 n
cq 688128 out
Feb 28 07:57:55 av kernel: [255241.198235]          res 40/00:e0:58:1e:dc/00:00:01:00:00/40 Emask 0x
10 (ATA bus error)
Feb 28 07:57:55 av kernel: [255241.198239] ata3.00: status: { DRDY }
Feb 28 07:57:55 av kernel: [255241.198242] ata3.00: failed command: WRITE FPDMA QUEUED
Feb 28 07:57:55 av kernel: [255241.198250] ata3.00: cmd 61/b8:c0:c8:cd:ef/03:00:06:00:00/40 tag 24 n
cq 487424 out
Feb 28 07:57:55 av kernel: [255241.198250]          res 40/00:e0:58:1e:dc/00:00:01:00:00/40 Emask 0x
10 (ATA bus error)
Feb 28 07:57:55 av kernel: [255241.198253] ata3.00: status: { DRDY }
Feb 28 07:57:55 av kernel: [255241.198257] ata3.00: failed command: WRITE FPDMA QUEUED
Feb 28 07:57:55 av kernel: [255241.198264] ata3.00: cmd 61/40:c8:b0:2d:64/05:00:06:00:00/40 tag 25 n
cq 688128 out
Feb 28 07:57:55 av kernel: [255241.198264]          res 40/00:e0:58:1e:dc/00:00:01:00:00/40 Emask 0x
10 (ATA bus error)
Feb 28 07:57:55 av kernel: [255241.198268] ata3.00: status: { DRDY }
Feb 28 07:57:55 av kernel: [255241.198271] ata3.00: failed command: WRITE FPDMA QUEUED
Feb 28 07:57:55 av kernel: [255241.198279] ata3.00: cmd 61/88:d0:f0:32:64/01:00:06:00:00/40 tag 26 n
cq 200704 out
Feb 28 07:57:55 av kernel: [255241.198279]          res 40/00:e0:58:1e:dc/00:00:01:00:00/40 Emask 0x
10 (ATA bus error)
Feb 28 07:57:55 av kernel: [255241.198282] ata3.00: status: { DRDY }
Feb 28 07:57:55 av kernel: [255241.198286] ata3.00: failed command: WRITE FPDMA QUEUED
Feb 28 07:57:55 av kernel: [255241.198293] ata3.00: cmd 61/08:d8:20:26:da/00:00:05:00:00/40 tag 27 n
cq 4096 out
Feb 28 07:57:55 av kernel: [255241.198293]          res 40/00:e0:58:1e:dc/00:00:01:00:00/40 Emask 0x
10 (ATA bus error)
Feb 28 07:57:55 av kernel: [255241.198297] ata3.00: status: { DRDY }
Feb 28 07:57:55 av kernel: [255241.198300] ata3.00: failed command: WRITE FPDMA QUEUED
Feb 28 07:57:55 av kernel: [255241.198307] ata3.00: cmd 61/08:e0:58:1e:dc/00:00:01:00:00/40 tag 28 n
cq 4096 out
Feb 28 07:57:55 av kernel: [255241.198307]          res 40/00:e0:58:1e:dc/00:00:01:00:00/40 Emask 0x
10 (ATA bus error)
Feb 28 07:57:55 av kernel: [255241.198311] ata3.00: status: { DRDY }
Feb 28 07:57:55 av kernel: [255241.198317] ata3: hard resetting link
Feb 28 07:57:59 av kernel: [255244.427656] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 28 07:57:59 av kernel: [255244.430700] ata3.00: configured for UDMA/33
Feb 28 07:57:59 av kernel: [255244.441789] ata3: EH complete
Feb 28 07:58:42 av kernel: [255287.669363] ata3: exception Emask 0x10 SAct 0x0 SErr 0x10200 action 0
xe frozen
Feb 28 07:58:42 av kernel: [255287.669369] ata3: irq_stat 0x00400000, PHY RDY changed
Feb 28 07:58:42 av kernel: [255287.669372] ata3: SError: { Persist PHYRdyChg }
Feb 28 07:58:42 av kernel: [255287.669378] ata3: hard resetting link
Feb 28 07:58:45 av kernel: [255291.154286] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 28 07:58:45 av kernel: [255291.157273] ata3.00: configured for UDMA/33
Feb 28 07:58:45 av kernel: [255291.168304] ata3: EH complete
Feb 28 08:00:43 av kernel: [255409.054157] ata3: exception Emask 0x10 SAct 0x0 SErr 0x10200 action 0
xe frozen
Feb 28 08:00:43 av kernel: [255409.054164] ata3: irq_stat 0x00400000, PHY RDY changed
Feb 28 08:00:43 av kernel: [255409.054168] ata3: SError: { Persist PHYRdyChg }
Feb 28 08:00:43 av kernel: [255409.054175] ata3: hard resetting link
Feb 28 08:00:46 av kernel: [255412.385122] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 28 08:00:46 av kernel: [255412.388149] ata3.00: configured for UDMA/33
Feb 28 08:00:46 av kernel: [255412.399080] ata3: EH complete
Feb 28 08:01:06 av kernel: [255432.051751] ata3: exception Emask 0x10 SAct 0x0 SErr 0x10200 action 0
xe frozen
Feb 28 08:01:06 av kernel: [255432.051760] ata3: irq_stat 0x00400000, PHY RDY changed
Feb 28 08:01:06 av kernel: [255432.051765] ata3: SError: { Persist PHYRdyChg }
Feb 28 08:01:06 av kernel: [255432.051773] ata3: hard resetting link
Feb 28 08:01:09 av kernel: [255435.434394] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 28 08:01:09 av kernel: [255435.437459] ata3.00: configured for UDMA/33
Feb 28 08:01:09 av kernel: [255435.448464] ata3: EH complete
Feb 28 08:06:57 av kernel: [255783.997284] ata3: exception Emask 0x10 SAct 0x0 SErr 0x10200 action 0
xe frozen
Feb 28 08:06:57 av kernel: [255783.997292] ata3: irq_stat 0x00400000, PHY RDY changed
Feb 28 08:06:57 av kernel: [255783.997308] ata3: SError: { Persist PHYRdyChg }
Feb 28 08:06:57 av kernel: [255783.997316] ata3: hard resetting link
Feb 28 08:07:00 av kernel: [255787.329140] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 28 08:07:00 av kernel: [255787.332199] ata3.00: configured for UDMA/33
Feb 28 08:07:00 av kernel: [255787.343115] ata3: EH complete
Feb 28 08:07:21 av kernel: [255807.619920] ata3: exception Emask 0x10 SAct 0x0 SErr 0x10200 action 0
xe frozen
Feb 28 08:07:21 av kernel: [255807.619929] ata3: irq_stat 0x00400000, PHY RDY changed
Feb 28 08:07:21 av kernel: [255807.619935] ata3: SError: { Persist PHYRdyChg }
Feb 28 08:07:21 av kernel: [255807.619943] ata3: hard resetting link
Feb 28 08:07:24 av kernel: [255811.002509] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 28 08:07:24 av kernel: [255811.005421] ata3.00: configured for UDMA/33
Feb 28 08:07:24 av kernel: [255811.016470] ata3: EH complete
Feb 28 08:07:42 av kernel: [255829.007258] ata3: exception Emask 0x10 SAct 0x0 SErr 0x10200 action 0
xe frozen
Feb 28 08:07:42 av kernel: [255829.007267] ata3: irq_stat 0x00400000, PHY RDY changed
Feb 28 08:07:42 av kernel: [255829.007272] ata3: SError: { Persist PHYRdyChg }
Feb 28 08:07:42 av kernel: [255829.007290] ata3: hard resetting link
Feb 28 08:07:45 av kernel: [255832.389965] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 28 08:07:45 av kernel: [255832.392860] ata3.00: configured for UDMA/33
Feb 28 08:07:45 av kernel: [255832.403934] ata3: EH complete
Feb 28 08:09:16 av kernel: [255922.909678] ata3: exception Emask 0x10 SAct 0x0 SErr 0x10200 action 0
xe frozen
Feb 28 08:09:16 av kernel: [255922.909682] ata3: irq_stat 0x00400000, PHY RDY changed
Feb 28 08:09:16 av kernel: [255922.909684] ata3: SError: { Persist PHYRdyChg }
Feb 28 08:09:16 av kernel: [255922.909688] ata3: hard resetting link
Feb 28 08:09:19 av kernel: [255926.240832] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 28 08:09:19 av kernel: [255926.243780] ata3.00: configured for UDMA/33
Feb 28 08:09:19 av kernel: [255926.254835] ata3: EH complete
Feb 28 08:14:57 av kernel: [256264.507432] ata3: exception Emask 0x10 SAct 0x0 SErr 0x10200 action 0
xe frozen
Feb 28 08:14:57 av kernel: [256264.507451] ata3: irq_stat 0x00400000, PHY RDY changed
Feb 28 08:14:57 av kernel: [256264.507457] ata3: SError: { Persist PHYRdyChg }
Feb 28 08:14:57 av kernel: [256264.507464] ata3: hard resetting link
Feb 28 08:15:00 av kernel: [256267.838515] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 28 08:15:00 av kernel: [256267.841351] ata3.00: configured for UDMA/33
Feb 28 08:15:00 av kernel: [256267.852558] ata3: EH complete
Feb 28 08:15:02 av kernel: [256269.883719] ata3: exception Emask 0x10 SAct 0x0 SErr 0x40c0200 action
 0xe frozen
Feb 28 08:15:02 av kernel: [256269.883725] ata3: irq_stat 0x00000040, connection status changed
Feb 28 08:15:02 av kernel: [256269.883729] ata3: SError: { Persist CommWake 10B8B DevExch }
Feb 28 08:15:02 av kernel: [256269.883734] ata3: hard resetting link

```


Basically... the HD keeps clicking. And when it really gets bad, it seems to freeze the entire system and/or stops opening programs. So it's pretty bad when it starts acting up.


In any case, I've upgraded my kernel to 4.x to improve other issues (like power) ... even though I think the HD problem actually stopped somewhere in the 3.x versions. But now that it's back ... I finally found out that this is a common problem with my drive. And from what I read, I think I need to patch the kernel, but since I have no experience with that ... I'm a little freaked out at the thought of messing with UbuntuStudio's RT kernel. So I tried to install the low-latency Xenial kernel from Synaptic, but didn't meet the dependencies and couldn't:(


```
linux-image-lowlatency-lts-xenial:
Depends: linux-image-4.4.0-4-lowlatency  but it is not installable
```


As for the "Workaround [patch]("https://bugzilla.kernel.org/attachment.cgi?id=183241") for kernel 4.0+" at Bugzilla ... I'm not sure what to do, since I'm running Wiley's kernel. Can I ... or no ... and if so, how?

```
$uname -a

Linux av 4.2.0-30-lowlatency #35~14.04.1-Ubuntu SMP PREEMPT Fri Feb 19 16:20:56 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```


The other thing I saw, is the actual [DL page of debs]("http://ubuntuhandbook.org/index.php/2016/01/how-to-install-linux-kernel-4-4-in-ubuntu/") for the 4.4.0 low latency kernel. Is it okay to install, and how would I go about that if I'm already missing dependencies for the other Xenial kernel?

-----

Thanks for looking! I appreciate any help here. Baby steps are good :)

---

