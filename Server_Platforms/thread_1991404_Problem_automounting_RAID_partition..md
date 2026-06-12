---
title: "Problem auto/mounting RAID partition."
date: 2012-05-30
forum: Server Platforms
---

### Post by p2bc on 2012-05-30
Setup:
The server has 6 drives -
Drive 1(sde): /w two Partitions
 - 1st Partition(sde1) :  /boot
 - 2nd Partition(sde2): LVM Encryption ( 4 LVMs)
  -- / (root) (ie lv-root)
  -- /usr       (ie lv-usr)
  -- /var       (ie lv-var)
  -- /tmp     (ie lv-tmp)

Drive 2 (sdf): /w one Partition
 - LVM Encrypted
 -- /swap    (ie lv-swap)

Drive 3-6(sda,sdb,sdc,sdd): (Software RAID 10) (Auto configure Ubuntu Server LTS 10.04 Alternative)
 - LVM Encrypted
 -- /home   (ie lv-home)
                                           
All  this was done a year ago, and has worked great with no problems,  upgrades and all. About a month ago I did an upgrade, and that  it when  things went awry. Did the standard restart to implement the upgrades and  the /home could not be mounted automatically, or manually as it turns  out.

Here is a list of things that  I can think of, and tried to diagnose the  problem. I can start the system and it functions, just do not have a  /home section since it the this partition that is on the RAID.

```

root@Server:~# mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.

root@Server:~# mdadm -A /dev/md0
mdadm: no devices found for /dev/md0

root@Server:~# sudo mdadm --assemble --scan
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.

root@Server:~# sudo mdadm --assemble --scan /dev/md0
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.

root@Server:~# sudo mdadm --assemble --scan /dev/md1
mdadm: /dev/md1 not identified in config file.

```As you will see with the fdisk, all 4 drives are there.

```

root@Server:~# cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid10 num-devices=4 UUID=45bf4c6f:50ba23a9:0d896258:695b04d0

# This file was auto-generated on Fri, 25 Nov 2011 15:11:06 -0500
# by mkconf $Id$

``````
root@Server:~# df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/Main-lv--root
                       3745360   1094956   2460148  31% /
none                   4091736       280   4091456   1% /dev
none                   4096720         0   4096720   0% /dev/shm
none                   4096720       248   4096472   1% /var/run
none                   4096720         0   4096720   0% /var/lock
none                   4096720         0   4096720   0% /lib/init/rw
/dev/sde1                93207     74013     14382  84% /boot
/dev/mapper/Main-lv--tmp
                       4047808     73568   3768624   2% /tmp
/dev/mapper/Main-lv--usr
                       3745360   1021412   2533692  29% /usr
/dev/mapper/Main-lv--var
                       3745360    260976   3294128   8% /var

``````

root@Server:~# ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 2012-05-30 12:48 /dev/sda
brw-rw---- 1 root disk 8,  1 2012-05-30 13:51 /dev/sda1
brw-rw---- 1 root disk 8, 16 2012-05-30 12:48 /dev/sdb
brw-rw---- 1 root disk 8, 17 2012-05-30 13:51 /dev/sdb1
brw-rw---- 1 root disk 8, 32 2012-05-30 12:48 /dev/sdc
brw-rw---- 1 root disk 8, 33 2012-05-30 13:51 /dev/sdc1
brw-rw---- 1 root disk 8, 48 2012-05-30 13:48 /dev/sdd
brw-rw---- 1 root disk 8, 49 2012-05-30 13:51 /dev/sdd1
brw-rw---- 1 root disk 8, 64 2012-05-30 12:47 /dev/sde
brw-rw---- 1 root disk 8, 65 2012-05-30 12:47 /dev/sde1
brw-rw---- 1 root disk 8, 66 2012-05-30 12:47 /dev/sde2
brw-rw---- 1 root disk 8, 80 2012-05-30 12:47 /dev/sdf
brw-rw---- 1 root disk 8, 81 2012-05-30 12:47 /dev/sdf1

root@Server:~# ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 25 2012-05-30 12:47 2fbb4d60-86e2-48af-864e-bf802ebbbfd5 -> ../../mapper/Main-lv--usr
lrwxrwxrwx 1 root root 26 2012-05-30 12:47 4109b8ca-efcc-488b-ac36-b6376569b5a4 -> ../../mapper/Main-lv--root
lrwxrwxrwx 1 root root 26 2012-05-30 12:47 6b8af98f-0fb8-4692-a95e-634ceac572b5 -> ../../mapper/Swap-lv--swap
lrwxrwxrwx 1 root root 25 2012-05-30 12:47 86880682-c7cc-48be-a887-772148c9708d -> ../../mapper/Main-lv--var
lrwxrwxrwx 1 root root 25 2012-05-30 12:47 a2a70916-8ade-4d26-95af-786c17efb23d -> ../../mapper/Main-lv--tmp
lrwxrwxrwx 1 root root 10 2012-05-30 12:47 ffa5fa7c-215e-4d53-95c6-ac203d171ad6 -> ../../sde1

root@Server:~# blkid /dev/sd*
/dev/sda1: UUID="45bf4c6f-50ba-23a9-0d89-6258695b04d0" TYPE="linux_raid_member" 
/dev/sdb1: UUID="45bf4c6f-50ba-23a9-0d89-6258695b04d0" TYPE="linux_raid_member" 
/dev/sdc1: UUID="45bf4c6f-50ba-23a9-0d89-6258695b04d0" TYPE="linux_raid_member" 
/dev/sdd1: UUID="45bf4c6f-50ba-23a9-0d89-6258695b04d0" TYPE="linux_raid_member" 
/dev/sde1: UUID="ffa5fa7c-215e-4d53-95c6-ac203d171ad6" TYPE="ext4" 
/dev/sde2: UUID="RpYpqe-0gBW-0FlR-iRoH-H4Z7-NTKb-hAv3qE" TYPE="LVM2_member" 
/dev/sdf1: UUID="YLhLrN-0jOd-Nv5N-A0iJ-34T3-WYyM-52Udob" TYPE="LVM2_member"

``````

root@Server:~# ls -l /dev/md*
brw-rw---- 1 root disk 9, 0 2012-05-30 13:51 /dev/md0
brw-rw---- 1 root disk 9, 1 2012-05-30 12:56 /dev/md1

``````

root@Server:~# fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243202  1953514583+  ee  GPT

Disk /dev/sdf: 8127 MB, 8127512576 bytes
252 heads, 32 sectors/track, 1968 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007190c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        1969     7934976   8e  Linux LVM

Disk /dev/sde: 16.0 GB, 16005464064 bytes
64 heads, 32 sectors/track, 15264 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000468f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           2          95       96256   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sde2              96       15263    15532032   8e  Linux LVM
Partition 2 does not end on cylinder boundary.

``````

root@Server:~# sudo mdadm --assemble --force /dev/md0
mdadm: no devices found for /dev/md0

```I  have read about as much as I did when I research all this for my  initial setup. I am sure it is simply something I have overlooked. I  just don't know what or where to begin. Everything say that this should  do it. It says 2 drives are missing but df and fdisk both show all the  drives.

If anyone can offer a point of view or suggestion I have not thought of I would greatly appreciate any advice.

Oh and I did check the log files (/var/log/messages) there a few errors, nothing that stands out a blaring obvious as to be directly related to this problem. I can submit them but would take up a lot or room.

---

### Post by cmont899 on 2012-05-30
Looks to be LVM not software raid. Whats the output of:

```
lvdisplay

```

---

### Post by cmont899 on 2012-05-30
Also what are the contents of /etc/fstab

---

### Post by p2bc on 2012-05-30
```

root@Server:~# lvdisplay
  --- Logical volume ---
  LV Name                /dev/Swap/lv-swap
  VG Name                Swap
  LV UUID                BkCMef-pfe7-vreD-1FTb-ftnp-Wi1C-cTYGoU
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                7.57 GiB
  Current LE             1937
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:0
   
  --- Logical volume ---
  LV Name                /dev/Main/lv-root
  VG Name                Main
  LV UUID                BrxsbM-8ADf-QpKO-U9nr-VGiR-66g1-aS8aVG
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                3.63 GiB
  Current LE             929
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:1
   
  --- Logical volume ---
  LV Name                /dev/Main/lv-usr
  VG Name                Main
  LV UUID                qgcT1z-VKT0-SnjL-WDIb-kk36-8H2e-spOv3O
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                3.63 GiB
  Current LE             929
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:2
   
  --- Logical volume ---
  LV Name                /dev/Main/lv-var
  VG Name                Main
  LV UUID                TGPLAW-x1Fq-Mas2-yQGZ-EZvb-Ynef-Tt8gdx
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                3.63 GiB
  Current LE             929
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:3
   
  --- Logical volume ---
  LV Name                /dev/Main/lv-tmp
  VG Name                Main
  LV UUID                9oeYyB-JBiH-cmKA-3fRh-uss9-2hvq-9xXK3O
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                3.92 GiB
  Current LE             1004
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:4


``````

root@Server:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/Main-lv--root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sde1 during installation
UUID=ffa5fa7c-215e-4d53-95c6-ac203d171ad6 /boot           ext4    defaults        0       2
/dev/mapper/Home-lv--home /home           ext4    defaults        0       2
/dev/mapper/Main-lv--tmp /tmp            ext4    defaults        0       2
/dev/mapper/Main-lv--usr /usr            ext4    defaults        0       2
/dev/mapper/Main-lv--var /var            ext4    defaults        0       2
/dev/mapper/Swap-lv--swap none            swap    sw              0       0
none /cgroup cgroup defaults 0 0

```
Thanks

---

### Post by rubylaser on 2012-05-30
It's LVM on top of mdadm.  What's the output of this?

```
mdadm -E /dev/sd[abcd]1
```
and
```
cat /proc/mdstat
```

If all of your disks are healthy (I assume you ran a smart test on each of them already), then it should be as simple as reassembling the array like this, but please post the results of the above commands first before running this.

```
mdadm --assemble /dev/md0 /dev/sd[abcd]1
```

---

### Post by p2bc on 2012-05-30
```

root@Server:~# mdadm -E /dev/sd[abcd]1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 45bf4c6f:50ba23a9:0d896258:695b04d0
  Creation Time : Thu Jun 23 11:19:36 2011
     Raid Level : raid10
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026816 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr  2 18:21:27 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : c877eb93 - correct
         Events : 432

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 45bf4c6f:50ba23a9:0d896258:695b04d0
  Creation Time : Thu Jun 23 11:19:36 2011
     Raid Level : raid10
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026816 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr  2 18:21:27 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : c877eba5 - correct
         Events : 432

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 45bf4c6f:50ba23a9:0d896258:695b04d0
  Creation Time : Thu Jun 23 11:19:36 2011
     Raid Level : raid10
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026816 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Feb  5 07:34:38 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : c82c3c02 - correct
         Events : 358

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 45bf4c6f:50ba23a9:0d896258:695b04d0
  Creation Time : Thu Jun 23 11:19:36 2011
     Raid Level : raid10
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026816 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Feb  5 07:34:38 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : c82c3c14 - correct
         Events : 358

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1

```

```

root@Server:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sda1[0](S) sdd1[3](S) sdb1[1](S) sdc1[2](S)
      7814053632 blocks
       
unused devices: <none>

```

---

### Post by p2bc on 2012-05-30
I did not think to run smart test on them because I enable SmartD on them when I set everything up with 3 different types of notifications if something failed and I just double check and got none of them.

I am a bit taken back on the "faulty removed" from the [FONT=monospace]mdadm -E /dev/sd[abcd]1
because it was running fine until the restart after the last system upgrade
[/FONT]

---

### Post by rubylaser on 2012-05-30
As you can see by the event counters on the 4 drives, sdc and sdd have lower counters, so those are the two disks that fell out of the array.  That doesn't necessarily mean that they're bad (could be a bad SATA controller, backplane, etc).  I would take a look at the smart data for those two disks and check for UDMA_CRC_ERRORS and other high values to rule out disk failure or bad SATA cables as the issue.
```
smartctl -a /dev/sdc
smartctl -a /dev/sdd
```

The (S) is a bit misleading here.  When an array is 'inactive', all devices are marked as '(S)', because they are not currently active (nothing is as the whole array is inactive).

The first thing I would try to do is stop the array and reassemble it like this.
```
sudo -i
mdadm --stop /dev/md0
mdadm --assemble /dev/md0 /dev/sd[abcd]1
```

If that works, I'd update your initramfs and reboot and see if it comes back up.
```
update-initramfs -u
```

---

### Post by p2bc on 2012-05-30
```

root@Server:~# smartctl -a /dev/sdc
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WCAZA5693418
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed May 30 20:14:15 2012 EDT
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
data collection:          (36000) seconds.
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
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 255) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   253   253   021    Pre-fail  Always       -       1008
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       68
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       3692
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       66
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       63
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       2600
194 Temperature_Celsius     0x0022   109   090   000    Old_age   Always       -       41
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      3502         -
# 2  Short offline       Completed without error       00%      3496         -
# 3  Short offline       Completed without error       00%      3469         -
# 4  Short offline       Completed without error       00%      3445         -
# 5  Short offline       Completed without error       00%      3421         -
# 6  Short offline       Completed without error       00%      3397         -
# 7  Short offline       Completed without error       00%      3373         -
# 8  Short offline       Completed without error       00%      3349         -
# 9  Extended offline    Completed without error       00%      3335         -
#10  Short offline       Completed without error       00%      3325         -
#11  Short offline       Completed without error       00%      3301         -
#12  Short offline       Completed without error       00%      3277         -
#13  Short offline       Completed without error       00%      3253         -
#14  Short offline       Completed without error       00%      3229         -
#15  Short offline       Completed without error       00%      3205         -
#16  Short offline       Completed without error       00%      3181         -
#17  Extended offline    Completed without error       00%      3167         -
#18  Short offline       Completed without error       00%      3157         -
#19  Short offline       Completed without error       00%      3133         -
#20  Short offline       Completed without error       00%      3109         -
#21  Short offline       Completed without error       00%      3086         -

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

```

root@Server:~# smartctl -a /dev/sdd
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WCAZA5741587
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed May 30 20:15:46 2012 EDT
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
data collection:          (40800) seconds.
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
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 255) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   253   253   021    Pre-fail  Always       -       1050
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       68
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       4667
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       66
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       64
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       2642
194 Temperature_Celsius     0x0022   109   089   000    Old_age   Always       -       41
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      3511         -
# 2  Short offline       Completed without error       00%      3503         -
# 3  Short offline       Completed without error       00%      3477         -
# 4  Short offline       Completed without error       00%      3453         -
# 5  Short offline       Completed without error       00%      3429         -
# 6  Short offline       Completed without error       00%      3405         -
# 7  Short offline       Completed without error       00%      3381         -
# 8  Short offline       Completed without error       00%      3357         -
# 9  Extended offline    Completed without error       00%      3343         -
#10  Short offline       Completed without error       00%      3333         -
#11  Short offline       Completed without error       00%      3309         -
#12  Short offline       Completed without error       00%      3285         -
#13  Short offline       Completed without error       00%      3261         -
#14  Short offline       Completed without error       00%      3237         -
#15  Short offline       Completed without error       00%      3213         -
#16  Short offline       Completed without error       00%      3189         -
#17  Extended offline    Completed without error       00%      3176         -
#18  Short offline       Completed without error       00%      3165         -
#19  Short offline       Completed without error       00%      3141         -
#20  Short offline       Completed without error       00%      3118         -
#21  Short offline       Completed without error       00%      3094         -

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

---

### Post by p2bc on 2012-05-30
```

root@Server:~# mdadm --stop /dev/md0
mdadm: stopped /dev/md0
root@Server:~# mdadm --assemble /dev/md0 /dev/sd[abcd]1
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.

```

---

### Post by p2bc on 2012-05-30
Ok, I am not liking what I am seeing, call me jumping the gun but I am taking it that I am s.o.l. My question is, if a RAID10 is  basically a RAID0 from 2x RAID1, and since in a RAID1 you can lose one of the two drives is there a way to  know which SDC and SDD in the case are.

Example1:         RAID0 (md0)
                               /           \
 RAID1(sda + sdb)         RAID1(sdc + sdd)

Example2:         RAID0 (md0)
                               /           \
 RAID1(sda + sdc)         RAID1(sdb + sdd)

In example1 I am pretty much s.o.l. In example2 I can replace sdc and sdd.

I am going to ask the question, but I think I know the answer, which means I am s.o.l, but is there a standard way that a RAID10 it formed or can it vary, and if so how do we determine which drives form each sub RAID.

---

### Post by rubylaser on 2012-05-30
You are correct in saying that you have had both disks drop out of one of your mirrored stripes so mdadm is not allowing it to re-assemble.  There are two other things to try before giving up (this is the first one :) ).

```
mdadm --stop /dev/md0
mdadm --assemble --scan -fv
```

Let me know how that goes.

---

### Post by p2bc on 2012-05-31
```

root@Server:~# mdadm --stop /dev/md0
mdadm: stopped /dev/md0

root@Server:~# mdadm --assemble --scan -fv
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/block/251:4: Device or resource busy
mdadm: /dev/block/251:4 has wrong uuid.
mdadm: cannot open device /dev/sdf1: Device or resource busy
mdadm: /dev/sdf1 has wrong uuid.
mdadm: cannot open device /dev/sdf: Device or resource busy
mdadm: /dev/sdf has wrong uuid.
mdadm: cannot open device /dev/block/251:3: Device or resource busy
mdadm: /dev/block/251:3 has wrong uuid.
mdadm: cannot open device /dev/block/251:2: Device or resource busy
mdadm: /dev/block/251:2 has wrong uuid.
mdadm: cannot open device /dev/block/251:1: Device or resource busy
mdadm: /dev/block/251:1 has wrong uuid.
mdadm: cannot open device /dev/root: Device or resource busy
mdadm: /dev/root has wrong uuid.
mdadm: cannot open device /dev/sde2: Device or resource busy
mdadm: /dev/sde2 has wrong uuid.
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: /dev/sde1 has wrong uuid.
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sde has wrong uuid.
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdd has wrong uuid.
mdadm: no RAID superblock on /dev/sdb
mdadm: /dev/sdb has wrong uuid.
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdc has wrong uuid.
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sda has wrong uuid.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sda1 is identified as a member of /dev/md0, slot 0.
mdadm: forcing event count in /dev/sdc1(2) from 358 upto 432
mdadm: forcing event count in /dev/sdd1(3) from 358 upto 432
mdadm: clearing FAULTY flag for device 2 in /dev/md0 for /dev/sdc1
mdadm: clearing FAULTY flag for device 0 in /dev/md0 for /dev/sdd1
mdadm: SET_ARRAY_INFO failed for /dev/md0: Device or resource busy
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/block/251:4: Device or resource busy
mdadm: cannot open device /dev/sdf1: Device or resource busy
mdadm: cannot open device /dev/sdf: Device or resource busy
mdadm: cannot open device /dev/block/251:3: Device or resource busy
mdadm: cannot open device /dev/block/251:2: Device or resource busy
mdadm: cannot open device /dev/block/251:1: Device or resource busy
mdadm: cannot open device /dev/root: Device or resource busy
mdadm: cannot open device /dev/sde2: Device or resource busy
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sdd1 is not built for host Server.
mdadm: no recogniseable superblock on /dev/sdd
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy

```
OK, well my two cents, besides ???, ...actually I will wait to see what you say because I am not totally sure how to formulate the thought into a statement.

Oh and on another thought should I be doing tis from a LiveCD, and not the root system itself. Wait how would I do that I would have to chroot into the system anyways from the LiveCD, don't mind my ramblings.

---

### Post by rubylaser on 2012-05-31
These lines are potentially good news :)

```
mdadm: forcing event count in /dev/sdc1(2) from 358 upto 432
mdadm: forcing event count in /dev/sdd1(3) from 358 upto 432
mdadm: clearing FAULTY flag for device 2 in /dev/md0 for /dev/sdc1
mdadm: clearing FAULTY flag for device 0 in /dev/md0 for /dev/sdd1
```

It brought the event counter up for those two disks.  Can you let me see this again?

```
cat /proc/mdstat
```
and
```
mdadm -E /dev/sd[abcd]1
```

---

### Post by p2bc on 2012-05-31
```

root@Server:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid10 sdb1[1] sdd1[3] sda1[0] sdc1[2]
      3907026816 blocks 64K chunks 2 near-copies [4/4] [UUUU]
      
unused devices: <none>

```

```

root@Server:~# mdadm -E /dev/sd[abcd]1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 45bf4c6f:50ba23a9:0d896258:695b04d0
  Creation Time : Thu Jun 23 11:19:36 2011
     Raid Level : raid10
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026816 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr  2 18:21:27 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : c877eb8d - correct
         Events : 432

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      active sync
   3     3       0        0        3      active sync
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 45bf4c6f:50ba23a9:0d896258:695b04d0
  Creation Time : Thu Jun 23 11:19:36 2011
     Raid Level : raid10
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026816 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr  2 18:21:27 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : c877eba5 - correct
         Events : 432

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 45bf4c6f:50ba23a9:0d896258:695b04d0
  Creation Time : Thu Jun 23 11:19:36 2011
     Raid Level : raid10
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026816 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Feb  5 07:34:38 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : c82c3c4c - correct
         Events : 432

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 45bf4c6f:50ba23a9:0d896258:695b04d0
  Creation Time : Thu Jun 23 11:19:36 2011
     Raid Level : raid10
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026816 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sun Feb  5 07:34:38 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : c82c3c5e - correct
         Events : 432

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1

```


And before I forget, thanks so much.  :)


And for those that saw this post before the edit, that is what we call a major brain fart. :)

---

### Post by rubylaser on 2012-05-31
I'm glad you got it working:)  If you have a chance, please mark the thread as solved under the Thread Tools at the top.

---

### Post by p2bc on 2012-05-31
I am sorry confusion, it is not solved. What I was refering to when I said edited and brain fart was my prior post had something of a "syntax error" which was my ... uhm mistake.
So I edited the post with the information that you asked for.

---

### Post by rubylaser on 2012-05-31
Okay, I'm confused now :)  Your array is up and running now at /dev/md0 with your disks all with the same event counter.  Are you not able to mount the logical volume on top of the array?

---

### Post by p2bc on 2012-05-31
UHM....

```

root@Server:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Thu Jun 23 11:19:36 2011
     Raid Level : raid10
     Array Size : 3907026816 (3726.03 GiB 4000.80 GB)
  Used Dev Size : 1953513408 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Apr  2 18:21:27 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2
     Chunk Size : 64K

           UUID : 45bf4c6f:50ba23a9:0d896258:695b04d0
         Events : 0.432

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1

root@Server:~# sudo mdadm --assemble --scan


```

.... yes ?!?!?!?!?!?!?!?!?!?!?!?!?!?!?!?!?.....<keep going>... ?!?!?!?!?!

I did nothing that has not been posted here so why all of a sudden...

---

### Post by p2bc on 2012-05-31
Ok, call me crazy. I almost lose a 2 terrabits of backups and information and I was, somewhat, cool with that. But something inexplicably failing and suddenly works again without the simplest explanation has set me off. What the heck!!!

And not that I am not thankful to everyone help. As always you guys show that there are still good people in the world that are willing to help pure strangers.

And it is not that I am not happy to have all the information again. It is the fact that it is fixed, and I have no idea how, and more to the point if it happens again I am no closer to understanding how to reproduce the desired effect.


Again thank you all for you time and help, I am just completely frustrated at ... the unknown.

---

### Post by darkod on 2012-05-31
I wouldn't say inexplicably. The

mdadm --assemble --scan -fv

seems to have done the job. Look at the extract of the command result rubylaser posted in post #14. It raised the counters of sdc1 and sdd1 which seems to have been the only problem stopping the array assembling.

After that the assembly went just fine and your array is back. I think rubylaser deserves the :popcorn:

---

### Post by p2bc on 2012-05-31
Please do not get me wrong, I do agree rubylaser deserves my thanks, and more for all his great help.


As for my frustration, the -f and -v option how is this different from --force, because I did try it with my earlier attempts that lead me to make this post in the first place. 

Anyways, if this or other unexplained things do occur again in the future I know I can always turn to the members of these forums for help. Thank you again for your time and help.

---

### Post by rubylaser on 2012-05-31
> **darkod said:**
> I wouldn't say inexplicably. The

mdadm --assemble --scan -fv

seems to have done the job. Look at the extract of the command result rubylaser posted in post #14. It raised the counters of sdc1 and sdd1 which seems to have been the only problem stopping the array assembling.

After that the assembly went just fine and your array is back. I think rubylaser deserves the :popcorn:

This is exactly what happened.  Ensuring that you have good backups should always be a top priority when you have data to protect.  And, as far as RAID reassembles go, this was really pretty straightforward.  We didn't have have to recreate the superblock metadata.

The -f option is the same as the --force option.  The main difference with this is that this has mdadm try to force assemble with all the block devices rather than what you have defined in your mdadm.conf file (that's why you see all the extra devices attempted in the verbose output previously).  You could have also done this and gotten the same results.

```
mdadm --stop /dev/md0
mdadm --assemble --force /dev/md0 /dev/sd[abcd]1

```

I hope that clears it up a little bit, and once again, the best part of this is you have your data back :)

---

