---
title: "zpool status and smartd disagreement"
date: 2020-10-05
forum: Server Platforms
---

### Post by larzeb on 2020-10-05
Looking at the output of systemctl status smartd:

```
Oct 05 07:18:54 server smartd[1802]: Device: /dev/sde [SAT], 146 Offline uncorrectable sectors
```

but zpool status says OK? /dev/sde highlighted below

```
$ sudo zpool status  pool: tank
 state: ONLINE
  scan: resilvered 5.68G in 0 days 00:01:05 with 0 errors on Sun Oct  4 11:28:03 2020
config:


    NAME                                            STATE     READ WRITE CKSUM
    tank                                            ONLINE       0     0     0
      raidz2-0                                      ONLINE       0     0     0
        ata-WDC_WD20EARX-00PASB0_WD-WMAZA8777267    ONLINE       0     0     0
        ata-WDC_WD20EFRX-68EUZN0_WD-WCC4M4NECAJA    ONLINE       0     0     0
        ata-Hitachi_HDS723020BLA642_MN1220F30RN6BD  ONLINE       0     0     0
**        ata-WDC_WD20EFRX-68EUZN0_WD-WCC4M0638620    ONLINE       0     0     0**
        ata-WDC_WD20EFRX-68EUZN0_WD-WCC4M7TS9A27    ONLINE       0     0     0
        ata-Hitachi_HDS723020BLA642_MN1220F30T6SJD  ONLINE       0     0     0


errors: No known data errors



```

How do I reconcile this apparent difference?

---

### Post by ameinild on 2020-10-07
Ok let's dig through this:

First, the line ending with: "146 Offline uncorrectable sectors" is a SMART attribute - it does not say the disk is offline. Rather, the disk has detected some sectors which has been marked as bad, and these sectors are not used. This is not uncommon, especially with older disks.

Do you run any SMART selftests with smartd (smartmontools)? If you do, then you'll get the overall assessment of disk health, including data for all SMART attributes and self test results. 
See here for more info on smartmontools, selftests etc. [https://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/](https://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/)

The disk will only be offline in the Zpool if it has critical failures that cause the entire disk to not operate any more - or if ZFS metadata is corrupt.

NB: The command to get a full SMART report for disk /dev/sde is: [FONT=courier new]

sudo smartctl -a /dev/sde[/FONT]

---

### Post by larzeb on 2020-10-07
Thanks for the detail. I am new at this.

I think this disk is old. I have run a test.

```
SMART Attributes Data Structure revision number: 16Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       32
  3 Spin_Up_Time            0x0027   173   171   021    Pre-fail  Always       -       4350
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       178
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   034   034   000    Old_age   Always       -       48753
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       178
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       152
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       727960
194 Temperature_Celsius     0x0022   115   101   000    Old_age   Always       -       32
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       146
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       2


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     48698         -
# 2  Short offline       Completed without error       00%      3041         -
# 3  Short offline       Completed without error       00%      3017         -
# 4  Short offline       Completed without error       00%      2993         -
# 5  Extended offline    Interrupted (host reset)      10%      2948         -
# 6  Short offline       Completed without error       00%      2921         -
# 7  Short offline       Completed without error       00%      2897         -
# 8  Short offline       Completed without error       00%      2873         -
# 9  Short offline       Completed without error       00%      2854         -
#10  Short offline       Completed without error       00%      2830         -
#11  Extended offline    Completed without error       00%      2805         -
#12  Short offline       Completed without error       00%      2758         -
#13  Short offline       Completed without error       00%      2734         -
#14  Short offline       Completed without error       00%      2710         -
#15  Short offline       Completed without error       00%      2686         -
#16  Short offline       Completed without error       00%      2662         -
#17  Extended offline    Completed without error       00%      2637         -
#18  Short offline       Completed without error       00%      2590         -
#19  Short offline       Completed without error       00%      2566         -
#20  Short offline       Completed without error       00%      2542         -
#21  Short offline       Completed without error       00%      2518         -



```

Should I worry?

---

### Post by ameinild on 2020-10-08
At the moment I reckon it doesn't show anything critical, but it has been running for 6 years. 

What I would do is configure smartd to run daily short tests and weekly extended tests (as was the case for the disk up until ~3000 hours - after that it ran no more self tests until you ran one manually).

As long as the self tests complete without warnings or errors, you're should be ok. Still, I would have a replacement disk lying ready in any case.

---

