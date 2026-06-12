---
title: "Random disk kicked from RAID (zentyal)"
date: 2013-02-26
forum: Server Platforms
---

### Post by Beliaz on 2013-02-26
I am running a "small" server with six Seagate ST2000DL003 set up in a Software RAID 6 with LVM on top. I have had Zentyal 2.0 64bit installed since spring 2011. In december 2011 i migrated to 2.2. 3.0 was released in november 2012, but no good migration tools were released, so I did a manual update (no format on /home).
 
After the update I loose disks from my RAID randomly. A couple per week. As soon as the RAID is up and running again one or two is being kicked.
 
I never had problem in Zentyal 2.x (based on Ubuntu 10.04 LTS) only in Zentyal 3.0 (based on Ubuntu 12.04 LTS). 
 
This is my setup:
MB: Supermicro X7SPA-HF-D525
RAM: 4GB
Primary HD: 2GB SD-card for /boot
Secondary HDs: 6 x Seagate ST2000DL003 attached to MB
PSU: Cooler Master Silent Pro Gold 600W
CASE: Lian Li PC-Q08R Mini Tower
 
What do You need to help me solve my problems?
mdstat:
```
root@zentyal:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid6 sdf1[6](S) sda1[7] sdd1[3] sdc1[2] sdg1[5] sdb1[1]
      7814053632 blocks level 6, 64k chunk, algorithm 2 [6/4] [_UUU_U]
      [==>..................]  recovery = 11.0% (216676324/1953513408) finish=1827.3min speed=15840K/sec
unused devices: <none>

```
syslog:
```
root@zentyal:~# grep -e sda -e sdf /var/log/syslog
Feb 26 19:01:52 zentyal kernel: [408209.543940] end_request: I/O error, dev sda, sector 2048
Feb 26 19:01:53 zentyal kernel: [408210.232419] sd 0:0:0:0: [sda] Unhandled error code
Feb 26 19:01:53 zentyal kernel: [408210.232429] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Feb 26 19:01:53 zentyal kernel: [408210.232440] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Feb 26 19:01:53 zentyal kernel: [408210.232480] end_request: I/O error, dev sda, sector 0
Feb 26 19:01:53 zentyal kernel: [408210.233128] sd 0:0:0:0: [sda] Unhandled error code
Feb 26 19:01:53 zentyal kernel: [408210.233135] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Feb 26 19:01:53 zentyal kernel: [408210.233143] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 00 08 00 00 00 08 00
Feb 26 19:01:53 zentyal kernel: [408210.233161] end_request: I/O error, dev sda, sector 2048
Feb 26 19:14:30 zentyal kernel: [    1.538281] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Feb 26 19:14:30 zentyal kernel: [    1.538289] sd 0:0:0:0: [sda] 4096-byte physical blocks
Feb 26 19:14:30 zentyal kernel: [    1.538550] sd 0:0:0:0: [sda] Write Protect is off
Feb 26 19:14:30 zentyal kernel: [    1.538561] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 26 19:14:30 zentyal kernel: [    1.538696] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 26 19:14:30 zentyal kernel: [    1.623126]  sda: sda1
Feb 26 19:14:30 zentyal kernel: [    1.623901] sd 0:0:0:0: [sda] Attached SCSI disk
Feb 26 19:14:30 zentyal kernel: [    2.818167] sd 4:0:0:0: [sdf] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Feb 26 19:14:30 zentyal kernel: [    2.818175] sd 4:0:0:0: [sdf] 4096-byte physical blocks
Feb 26 19:14:30 zentyal kernel: [    2.818416] sd 4:0:0:0: [sdf] Write Protect is off
Feb 26 19:14:30 zentyal kernel: [    2.818426] sd 4:0:0:0: [sdf] Mode Sense: 00 3a 00 00
Feb 26 19:14:30 zentyal kernel: [    2.818528] sd 4:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 26 19:14:30 zentyal kernel: [    2.888491]  sdf: sdf1
Feb 26 19:14:30 zentyal kernel: [    2.889253] sd 4:0:0:0: [sdf] Attached SCSI disk
Feb 26 19:14:30 zentyal kernel: [    3.467816] md: bind<sdf>
Feb 26 19:14:30 zentyal kernel: [    3.837624] md: bind<sda1>
Feb 26 19:14:30 zentyal kernel: [   39.188480] md: kicking non-fresh sda1 from array!
Feb 26 19:14:30 zentyal kernel: [   39.188497] md: unbind<sda1>
Feb 26 19:14:30 zentyal kernel: [   39.188653] md: export_rdev(sda1)
Feb 26 19:14:30 zentyal kernel: [   39.188753] md: kicking non-fresh sdf from array!
Feb 26 19:14:30 zentyal kernel: [   39.188765] md: unbind<sdf>
Feb 26 19:14:30 zentyal kernel: [   39.188837] md: export_rdev(sdf)

```
smartctl:
```
root@zentyal:~# smartctl -d sat -a /dev/sda -t short
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-38-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Green (Adv. Format)
Device Model:     ST2000DL003-9VT166
Serial Number:    5YD2C5X7
LU WWN Device Id: 5 000c50 02fd26c07
Firmware Version: CC45
User Capacity:    2 000 398 934 016 bytes [2,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue Feb 26 23:56:29 2013 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 241) Self-test routine in progress...
                                        10% of test remaining.
Total time to complete Offline
data collection:                (  612) seconds.
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
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x30b7) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   099   099   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       51
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   085   060   030    Pre-fail  Always       -       337709019
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       15571
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       51
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       4295032842
189 High_Fly_Writes         0x003a   063   063   000    Old_age   Always       -       37
190 Airflow_Temperature_Cel 0x0022   064   056   045    Old_age   Always       -       36 (Min/Max 35/36)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       43
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       51
194 Temperature_Celsius     0x0022   036   044   000    Old_age   Always       -       36 (0 14 0 0)
195 Hardware_ECC_Recovered  0x001a   024   010   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       127865471384782
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       565467124
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2525562635
SMART Error Log Version: 1
No Errors Logged
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Self-test routine in progress 10%     15571         -
# 2  Short offline       Aborted by host               10%     15570         -
# 3  Short offline       Completed without error       00%     15099         -
# 4  Short offline       Completed without error       00%     15094         -
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
=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 1 minutes for test to complete.
Test will complete after Tue Feb 26 23:57:30 2013
Use smartctl -X to abort test.
root@zentyal:~# smartctl -d sat -a /dev/sdb -t short
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-38-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda Green (Adv. Format)
Device Model:     ST2000DL003-9VT166
Serial Number:    5YD2C56S
LU WWN Device Id: 5 000c50 02fd24bf1
Firmware Version: CC45
User Capacity:    2 000 398 934 016 bytes [2,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue Feb 26 23:56:35 2013 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 241) Self-test routine in progress...
                                        10% of test remaining.
Total time to complete Offline
data collection:                (  623) seconds.
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
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x30b7) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   101   099   006    Pre-fail  Always       -       221360
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       51
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   084   060   030    Pre-fail  Always       -       327530500
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       15727
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       51
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       12885098519
189 High_Fly_Writes         0x003a   083   083   000    Old_age   Always       -       17
190 Airflow_Temperature_Cel 0x0022   065   057   045    Old_age   Always       -       35 (Min/Max 34/35)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       41
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       51
194 Temperature_Celsius     0x0022   035   043   000    Old_age   Always       -       35 (0 14 0 0)
195 Hardware_ECC_Recovered  0x001a   037   014   000    Old_age   Always       -       221360
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       38366942870895
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       1298865882
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3442311820
SMART Error Log Version: 1
No Errors Logged
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Self-test routine in progress 10%     15727         -
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
=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 1 minutes for test to complete.
Test will complete after Tue Feb 26 23:57:36 2013
Use smartctl -X to abort test.

```
Notice the Command_Timeout value. I looked through similar threads here but others value for that parameter is almost always 0...
 
Is Ubuntu 12.04 LTS less forgiving than 10.04 LTS for using Green HDDs in a Software RAID setup?
 
/ Bengt-Erik

---

### Post by tgalati4 on 2013-02-26
Green disks are usually not a good idea in RAID configurations.  You can use them in JBOD (just a bunch of disks) configuration, but the tolerances and demands of RAID would lead to problems.  Not unlike what you are experiencing.  There have been lots of kernel changes between 10.04 and 12.04, so yes, that is probably a factor.  Some errors that were ignored or repressed are now significant--and vice versa.

It's also possible that you simply need to reseat your SATA and power connectors.  Anything not handled by the kernel is a bad sign:

 [408210.232480] end_request: **I/O error**, dev sda, sector 0
Feb 26 19:01:53 zentyal kernel: [408210.233128] sd 0:0:0:0: [sda] **Unhandled error **code

---

### Post by Vegan on 2013-02-26
first the ST2000DL003 is not designed for RAID use

second, if you want a secure RAID, get a real RAID card with a hardware logic to do the RAID5/6 calculations

---

### Post by rubylaser on 2013-02-27
> **Vegan said:**
> first the ST2000DL003 is not designed for RAID use

second, if you want a secure RAID, get a real RAID card with a hardware logic to do the RAID5/6 calculations

A parity calculation done by a hardware RAID card is no more "secure" than a software RAID card.  It also costs much more than the free price of mdadm and locks you into a specific piece of hardware rather than being hardware neutral like mdadm.

---

### Post by Beliaz on 2013-02-27
My computer is finish rebuilding in about 10 hours. If I stop the computer, reseat all cables and then start the computer again, will it start from the beginning with the rebuilding or will it continue where it was (2/3 complete)?
 
/ Bengt-Erik

---

### Post by rubylaser on 2013-02-27
It will restart.  Just let the sync finish.

---

### Post by Beliaz on 2013-03-06
Ok. Took a few days longer than expected, since it started rebuilding a couple of times more.
Status now is:
```
root@zentyal:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid6 sdf1[4] sda1[6](F) sdd1[3] sdc1[2] sdg1[5] sdb1[1]
      7814053632 blocks level 6, 64k chunk, algorithm 2 [6/5] [_UUUUU]
unused devices: <none>
You have new mail in /var/mail/root
root@zentyal:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid6 sdf1[4] sda1[6](F) sdd1[3] sdc1[2] sdg1[5] sdb1[1]
      7814053632 blocks level 6, 64k chunk, algorithm 2 [6/5] [_UUUUU]
unused devices: <none>
```
What is the proper way to re-add a "failed" GPT disk (when I run SeaTools no errors were found)? This is how I've done it last time /dev/sdf1 failed:
```
parted /dev/sdg print

Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdg: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2000GB  2000GB                     raid
 
mdadm --manage /dev/md127 --fail /dev/sdf1
mdadm --manage /dev/md127 --remove /dev/sdf1
parted /dev/sdf print
parted /dev/sdf mklabel gpt
parted /dev/sdf mkpart ext2 1 2000GB
parted /dev/sdf set 1 raid on
parted /dev/sdf print
mdadm --manage /dev/md127 --add /dev/sdf1

parted /dev/sdf print
Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdf: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2000GB  2000GB               ext2  raid

```

/ Bengt-Erik

---

### Post by Beliaz on 2013-05-07
Still having the problem with disks falling out. Lately I also always boot into recovery console which asks me if I wan't to start system in degraded mode. This is not good, since I usually don't have physical access to the server.
I tried to reconfigure that with dpkg-reconfigure mdadm, but the changes did not solved it. I also had some problems with that the server is displaying some error after grub menu
```
error: no such device: 9b320c55-0a41-45c8-a97e-61aca0b52bd3.
error: no such disk.
error: no suitable mode found.
error: no video mode activated.
```
 I thought that I needed to update the grub.cfg, so I executed ```
grub-mkconfig -o /boot/grub/grub.cfg
```. I then got this printout:
```
error: found two disks with the index 4 for RAID md127.
error: found two disks with the index 4 for RAID md127.
Generating grub.cfg ...
error: found two disks with the index 4 for RAID md127.
error: found two disks with the index 4 for RAID md127.
error: found two disks with the index 4 for RAID md127.
error: found two disks with the index 4 for RAID md127.
error: found two disks with the index 4 for RAID md127.
error: found two disks with the index 4 for RAID md127.
error: found two disks with the index 4 for RAID md127.
error: found two disks with the index 4 for RAID md127.
error: found two disks with the index 4 for RAID md127.
error: found two disks with the index 4 for RAID md127.
error: found two disks with the index 4 for RAID md127.
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
error: found two disks with the index 4 for RAID md127.
error: found two disks with the index 4 for RAID md127.
error: found two disks with the index 4 for RAID md127.
error: found two disks with the index 4 for RAID md127.
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-39-generic
Found initrd image: /boot/initrd.img-3.2.0-39-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
error: found two disks with the index 4 for RAID md127.
done
```
[LIST=1]
[*]Can my problems be that two disks are having conflicts with each other? How do I solve this?
[*]Since I'm booting from SD-cart, should I install GRUB to SD-card (/dev/sde) or RAID-volume (/dev/md127)?
[*]How do I get rid of the error messages after GRUB menu.
[*]It looks like my server behaves differently every second reboot or if I shut down and restart manually. In one of the cases GRUB menu is shown without the count down before booting. I have to manually press enter. Then I will see the choise of starting in degraded mode. In the other case I got the choise of starting in degraded mode emediatly. Is that how it should be? GRUB menu only when cold booting?
[/LIST]

Thanks in advance / Bengt-Erik

---

### Post by fgouget on 2013-09-04
> **Beliaz said:**
> Still having the problem with disks falling out. Lately I also always boot into recovery console which asks me if I wan't to start system in degraded mode. This is not good, since I usually don't have physical access to the server.  I would put the blame for your woes squarely on the ST2000DL003 disks: they are known to randomly 'freeze' and Seagate does not care about it. [http://forums.storagereview.com/index.php/topic/29493-seagate-barracuda-green-2tb-review/page__view__findpost__p__274408](http://forums.storagereview.com/index.php/topic/29493-seagate-barracuda-green-2tb-review/page__view__findpost__p__274408)  And unlike other posters I wouldn't blame you one bit for picking these disks. Or they'd have to explain exactly what's different about disks meant to be used in software RAID arrays.  To mitigate the problems my recommendation would be to use RAID, as you do, and a write-intent bitmap to speed up the array rebuilds.

---

