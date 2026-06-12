---
title: "hdd fails to mount"
date: 2014-01-04
forum: Server Platforms
---

### Post by johans.postbox on 2014-01-04
Hi,

I have a strange issue.
I am running a 10.04 server and after the latest upgrade (kernel) one disk fails to mount.
It used to be part of a raid array, but that has been deleted.
Trying to mount manually fails with 
```
mount: /dev/sdc1 already mounted or /media/storage/ busy
```

tried to force it but to no success.

I suspect it could be some problem with th old raid setup still trying to use it or something (soft raid with mdadm) because when I run fsck on it I get this:
```
fsck from util-linux-ng 2.17.2
fsck: fsck.linux_raid_member: not found
fsck: Error 2 while executing fsck.linux_raid_member for /dev/sdc
```

Could it be update-initramfs that mess something up? That is run during kernel upgrade.

The drive is working fine when used in a usb-enclosure connected to other computer. It does not have the raid flag set anymore either, normal linux flag is set (0x83).

Any suggestions? Some lingering raid settings? Where would I find them? I see nothing strange in /etc/mdadm/mdadm.conf

Thanks
/Johan

---

### Post by sudodus on 2014-01-04
Welcome to the Ubuntu Forums :-)

I would try to wipe the first megabyte, overwrite with zeros using dd or rather [mkusb ]("http://ubuntuforums.org/showthread.php?t=1958073")to avoid writing to another disk). And after that repartition and reformat it with ***gparted*** (or a command line tool if you prefer that).

---

### Post by johans.postbox on 2014-01-05
Thanks, but I have actually been a member for a long time, but have not logged in since the change of login service, had to create a new account.

Anyway, I would prefer not to loose the data on it. I currently only have one backup of it (recently my other backup disk died during restore, hence I am *very *careful until I got at least one more backup).
And I did repartition and reformatted it and changed the flag from raid to normal linux when I took it out of raid duty. You mean there might be something else on the disk causing this behavior?

---

### Post by Bucky Ball on 2014-01-05
*Thread moved to **Server Platforms**.*

You might have more luck here.

---

### Post by sudodus on 2014-01-05
> **johans.postbox said:**
> Thanks, but I have actually been a member for a long time, but have not logged in since the change of login service, had to create a new account.

Anyway, I would prefer not to loose the data on it. I currently only have one backup of it (recently my other backup disk died during restore, hence I am *very *careful until I got at least one more backup).
And I did repartition and reformatted it and changed the flag from raid to normal linux when I took it out of raid duty. You mean there might be something else on the disk causing this behavior?

Yes, I have seen such cases at the Ubuntu Forums. But take your time and make a careful backup before wiping anything. And it was a good idea to move the thread to Server Platforms, so we can await more (and maybe better) advice :-)

---

### Post by rubylaser on 2014-01-05
If this disk used to have mdadm setup on it, and you happen to have it installed, just zero the superblock.  You won't lose any data as a result of this.  Also, could you provide us a look at the SMART data and a df -h and mount?

```

sudo -i
mdadm --zero-superblock /dev/sdc1
smartctl -a /dev/sdc
df -h
mount

```

If you don't have smartmontools or mdadm installed to do the above, just run this.
```

apt-get install smartmontools mdadm -y

```

---

### Post by johans.postbox on 2014-01-06
Zeroing the superblock did not work. My guess is that it is because of the same problem that makes it fail to mount, device busy?
```
mdadm --zero-superblock /dev/sdc1
mdadm: Couldn't open /dev/sdc1 for write - not zeroing
```

SMART data:
```

smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD1003FBYZ-010FB0
Serial Number:    WD-WCAW36611710
Firmware Version: 01.01V03
User Capacity:    1 000 204 886 016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Jan  6 14:35:08 2014 CET
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
data collection:                 (16680) seconds.
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
recommended polling time:        ( 164) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   175   175   021    Pre-fail  Always       -       4216
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       18
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1600
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       18
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       14
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       4
194 Temperature_Celsius     0x0022   113   102   000    Old_age   Always       -       34
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   199   000    Old_age   Always       -       64
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       1

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Conveyance offline  Completed without error       00%       490         -
# 2  Conveyance offline  Completed without error       00%       322         -
# 3  Extended offline    Completed without error       00%       251         -
# 4  Conveyance offline  Completed without error       00%       154         -

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

df and mount does not show that disk at all since it is not mounted.
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             135G   11G  118G   9% /
none                  1,9G  248K  1,9G   1% /dev
none                  2,0G     0  2,0G   0% /dev/shm
none                  2,0G  680K  2,0G   1% /var/run
none                  2,0G  4,0K  2,0G   1% /var/lock
none                  2,0G     0  2,0G   0% /lib/init/rw
/dev/sdd1             917G  486G  385G  56% /media/backup

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdd1 on /media/backup type ext4 (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw,relatime)
nfsd on /proc/fs/nfsd type nfsd (rw,relatime)

```

---

### Post by rubylaser on 2014-01-06
The first thing I would do is change the SATA cable on that disk and attach it to a different SATA head on the motherboard if you have any open.  UDMA_CRC_ERRORS are almost always a bad connection between the disk and motherboard.  After doing that, can you try to run a long SMART test on the disk?

```

smartctl -t long /dev/sdc

```

Also, what do your partitions look like on that disk?
```

fdisk /dev/sdc

```

Press "p" when that loads to view the partitions.  Please copy and paste them back here, and then quit fdisk.  Maybe the reason the fsck is complaining is that you have an fd flag on one of your partitions.  Also, when you tried to run the fsck did you tell it what type of filesystem the disk has (i.e. fsck.ext4 /dev/sdc1)?

---

### Post by johans.postbox on 2014-01-06
This was the fsck command I used: "fsck -n -y ext4 /dev/sdc"

And fdisk partition output:
```

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b45b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976760832   83  Linux

```

I will now swap sata connection with one of the other drives.

---

### Post by johans.postbox on 2014-01-06
This is the result of SMART long test after switching to a new sata port, UDMA_CRC_Error did not increase (I don't know it it would only by running the test, maybe some real read/write is needed to impact this value?):
```

smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD1003FBYZ-010FB0
Serial Number:    WD-WCAW36611710
Firmware Version: 01.01V03
User Capacity:    1 000 204 886 016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Jan  6 20:05:27 2014 CET
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
data collection:                 (16680) seconds.
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
recommended polling time:        ( 164) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   175   175   021    Pre-fail  Always       -       4225
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       19
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1606
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       19
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       14
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       5
194 Temperature_Celsius     0x0022   108   102   000    Old_age   Always       -       39
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   199   000    Old_age   Always       -       64
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      1605         -
# 2  Conveyance offline  Completed without error       00%       490         -
# 3  Conveyance offline  Completed without error       00%       322         -
# 4  Extended offline    Completed without error       00%       251         -
# 5  Conveyance offline  Completed without error       00%       154         -

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

Still not able to mount it :(

---

### Post by rubylaser on 2014-01-06
Your SMART values look okay, and I'm glad your counters didn't increase.  Do you still see the errors about the disk being mounted when try to mount it or mentions about linux_raid_member from fdisk?  Did you try to zero the superblock on the raw disk as well?  Above it's mentioning /dev/sdc not the partition.

```

mdadm --zero-superblock /dev/sdc

```

If that doesn't work, I'd probably boot from a live Ubuntu cd and see if you can mount it there.

---

### Post by johans.postbox on 2014-01-07
Still exactly the same behavior ;(
Changed from sdc to sdd when I changed sata port.

```

mount /dev/sdd1 /media/storage
mount: /dev/sdd1 already mounted or /media/storage busy

mdadm --zero-superblock /dev/sdd
mdadm: Couldn't open /dev/sdd for write - not zeroing

fsck -n -y ext4 /dev/sdd
fsck from util-linux-ng 2.17.2
fsck: fsck.linux_raid_member: not found
fsck: Error 2 while executing fsck.linux_raid_member for /dev/sdd

```

---

### Post by sudodus on 2014-01-07
I see that you have been trying a lot of things. Maybe you can connect the disk to another computer for example via an external box (eSATA or USB)? Or did you try running a live system as suggested by rubylaser in post #11?

Is there important information on the disk, that you need to extract from it? If nothing else works, there is ***PhotoRec*** as a last resort. Otherwise, I suggest again that you wipe it, because there might be something from the raid configuration, that makes it hard to mount.

---

### Post by johans.postbox on 2014-01-07
I can mount it without any problems on another computer using a usb enclosure.
I am pretty sure it will mount using a live cd as well since there, as far as I can tell, is nothing wrong with the drive.
I suspect the problem is somewhere else in the system, something is hogging the drive and preventing it from being mounted (device busy).
At least that's my somewhat educated guess ;)

I will try to zero the superblock when I have it in the usb-dock, posting result here later.

---

### Post by rubylaser on 2014-01-07
Take a look at it with lsof to see what is using it. Like this...
```

root@fileserver:~# lsof | grep sdd
jbd2/sdd1   824       root  cwd       DIR                8,1        4096          2 /
jbd2/sdd1   824       root  rtd       DIR                8,1        4096          2 /
jbd2/sdd1   824       root  txt   unknown                                           /proc/824/exe

```

---

### Post by johans.postbox on 2014-01-07
lsof | grep sdd
Shows nothing :(

---

### Post by rubylaser on 2014-01-07
> **johans.postbox said:**
> lsof | grep sdd
Shows nothing :(

It sounds like something is goofed up with your install or disk or a combination of both.  If this was me, I would first backup the data on the disk in question.  I would then write zeros to the misbehaving drive, once done, I would create a new filesystem on this drive, and then transfer the data over to it.

---

### Post by johans.postbox on 2014-01-07
Ok, I will first try to zero the superblock by connecting the drive to another computer (later today, at work now). If that also fails I guess I will have to wait for the additional backup drive to arrive and then wipe the troublesome disk clean.

---

### Post by johans.postbox on 2014-01-07
Woho! It worked! \\:D/

Thank you for all the help.

Zeroing the superblock by attaching it to another computer did the trick.

---

### Post by rubylaser on 2014-01-07
No problem, glad you got it working :)

---

