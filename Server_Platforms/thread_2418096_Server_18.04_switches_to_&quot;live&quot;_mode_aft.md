---
title: "Server 18.04 switches to &quot;live&quot; mode after unclean shutdown"
date: 2019-05-01
forum: Server Platforms
---

### Post by siesero on 2019-05-01
My server is acting up after an unclean shutdown earlier this week. 
When I SSH in, the welcome screen tells me I have 60 packages to update.
But after I do that and reboot, I am greeted with the same message and the same "last login" date of last week.

It appears that everything I do is reverted after every reboot.
Almost like I am running a "live" install which I am not. 
Any idea what could be causing this groundhog day situation?

---

### Post by siesero on 2019-05-01
As suggested in [this thread]("https://www.raspberrypi.org/forums/viewtopic.php?t=21330") please see the result of df down here. 
FWIW, my system is not running from a corrupted SD card but from SSD.

```
Filesystem                        1K-blocks     Used Available Use% Mounted on
udev                                4012344        0   4012344   0% /dev
tmpfs                                808592     1244    807348   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv 229132716 44209748 175550732  21% /
tmpfs                               4042948        0   4042948   0% /dev/shm
tmpfs                                  5120        0      5120   0% /run/lock
tmpfs                               4042948        0   4042948   0% /sys/fs/cgroup
/dev/loop0                            91648    91648         0 100% /snap/core/6818
/dev/loop1                            91392    91392         0 100% /snap/core/6673
/dev/loop2                            93184    93184         0 100% /snap/core/6350
/dev/loop3                           200192   200192         0 100% /snap/nextcloud/12753
/dev/sda2                            999320    77728    852780   9% /boot
/dev/sda1                            523248     6152    517096   2% /boot/efi
tmpfs                                808588        0    808588   0% /run/user/1000
```

---

### Post by #&amp;thj^% on 2019-05-01
Can you show us this also as added information: 
Please use code tags it helps us.
```
cat /etc/fstab
```
And also:
```
mount
```

---

### Post by siesero on 2019-05-01
Sure thing!

```

cat /etc/fstab 
UUID=b5374e8c-74e8-413f-8fd8-62e80d89f224 / ext4 defaults 0 0
UUID=042845a0-9234-4d01-9471-5b63636eb81b /boot ext4 defaults 0 0
UUID=6970-B8EE /boot/efi vfat defaults 0 0

```

```

mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4012344k,nr_inodes=1003086,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=808592k,mode=755)
/dev/mapper/ubuntu--vg-ubuntu--lv on / type ext4 (rw,relatime,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=31,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=15640)
mqueue on /dev/mqueue type mqueue (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
configfs on /sys/kernel/config type configfs (rw,relatime)
/var/lib/snapd/snaps/core_6818.snap on /snap/core/6818 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_6673.snap on /snap/core/6673 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_6350.snap on /snap/core/6350 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/nextcloud_12753.snap on /snap/nextcloud/12753 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sda2 on /boot type ext4 (rw,relatime,data=ordered)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
lxcfs on /var/lib/lxcfs type fuse.lxcfs (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other)
tmpfs on /run/snapd/ns type tmpfs (rw,nosuid,noexec,relatime,size=808592k,mode=755)
nsfs on /run/snapd/ns/nextcloud.mnt type nsfs (rw)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=808588k,mode=700,uid=1000,gid=1000)

```

---

### Post by #&amp;thj^% on 2019-05-01
Yep you have a strange set-up there, look at the difference between yours and mine: And Please don't use mine, it will break your system.;)
```
cat /etc/fstab
# /dev/sda4
UUID=5f99a7eb-5b70-4c03-a242-6e6eb06ca208	/         	**ext4      	rw,relatime	0 1**

# /dev/sda2
UUID=468e8275-6bad-45fc-99a0-ed2b77e30538	/boot     	**ext4      	rw,relatime	0 2**

# /dev/sda3
UUID=70e26944-69e8-4d18-8a7a-4da66ee8ca6c	none      	**swap      	defaults,pri=-2	0 0**


```
I would of thought to see something along the lines as below:
```
 contents of /etc/fstab:

mount -o remount,rw /dev/sdb6 /
```
Note: Instead of /dev/sdb6, use whatever device is valid for your drive.

Still waiting for this:
```
mount
```

---

### Post by siesero on 2019-05-01
I had pasted in the results of mount above already.

---

### Post by #&amp;thj^% on 2019-05-01
yes i see that now. Thanks.
Also I think it should look as "rw,relatime   0    2" but wait for others I run different systems at all times.
This from "man fstab":
```
DESCRIPTION
       The  file  fstab contains descriptive information about the filesystems
       the system can mount.  fstab is only read by programs, and not written;
       it is the duty of the system administrator to properly create and main&#8208;
       tain this file.  The order of records in  fstab  is  important  because
       fsck(8), mount(8), and umount(8) sequentially iterate through fstab do&#8208;
       ing their thing.

       Each filesystem is described on a separate line.  Fields on  each  line
       are separated by tabs or spaces.  Lines starting with '#' are comments.
       Blank lines are ignored.

       The following is a typical example of an fstab entry:

              LABEL=t-home2   /home      ext4    defaults,auto_da_alloc      0
              2

```
Please make a back-up first just for sanity's sake.
cd to the /etc directory on your hard disk:
```
cd /etc
sudo mv fstab fstab.bak
```
Also could be a corrupt /boot or /root from the UN-clean shutdown

---

### Post by siesero on 2019-05-02
> **1fallen said:**
> yes i see that now. Thanks.
Also I think it should look as "rw,relatime   0    2" but wait for others I run different systems at all times.

Please make a back-up first just for sanity's sake.
cd to the /etc directory on your hard disk:
```
cd /etc
sudo mv fstab fstab.bak
```
Also could be a corrupt /boot or /root from the UN-clean shutdown

Thanks for your help so far!
I have tried to change the pass flag in /etc/fstab to "1" but off course this change is also not retained after reboot.
Will try to hook my server up with a keyboard and monitor, boot into recovery and try again.

---

### Post by slickymaster on 2019-05-02
Thread moved to **Server Platforms** for a better fit

---

### Post by #&amp;thj^% on 2019-05-02
For problems like this I follow a procedure via:
There seems to be some different approaches, depending on your current problem:
[list]
    [*]Readonly by vi. If your file has :set readonly you can
       [*]Use :w! to force write, or
        [*]Issue :set noreadonly and then just use normal :w
    [*]A permission problem (sudo): you can't write but you have sudo rights.
        [*]Issue: :w !sudo tee %. This will write the buffer to tee, a command that receives pipe information and can write to files. And as tee is run with sudo powers, tee can modify the file.
    A permission problem (no sudo): you don't have rights to write the file and you don't have admin access.
        [*]Use :w! ~/tempfile.ext to write your changes to a temporary file and then take measures to move the temp file to the directory (send the temp file to the directory owner/admin).[/list]
What the command does:
```

    :w = Write a file.
    !sudo = Call shell sudo command.
    tee = The output of the vi/vim write command is redirected using tee.
    % = Triggers the use of the current filename.
    Simply put, the &#8216;tee&#8217; command is run as sudo and follows the vi/vim command on the current filename given.
```

Also have a look here: [https://stackoverflow.com/questions/2600783/how-does-the-vim-write-with-sudo-trick-work](https://stackoverflow.com/questions/2600783/how-does-the-vim-write-with-sudo-trick-work)
I have a long day today, but will check back to see how you are getting along. Good Luck

---

### Post by siesero on 2019-05-05
This appears to be more serious than I initially thought. I was unable to retain the edited fstab after a reboot in any way and decided to do a fresh install. But the installation failed because it could not remove the existing lvm partition. 
Even Parted running from a live usb was unable to wipe the (brand new) ssd. Or rather, deleting all partitions appear to complete successfully but they reappear after refreshing the screen! I am at a complete loss as to how this can happen but I am afraid it is a hardware failure......

---

### Post by siesero on 2019-05-06
To wrap this up, below the output from smartctl -a /dev/sda.It tells me the drive is expected to fail within 24 hours.Hope that this will be enough to get a replacement from the webstore I got this SSD from.

```
sudo smartctl -a /dev/sda
smartctl 6.6 2017-11-05 r4594 [x86_64-linux-4.19.0-4-amd64] (local build)
Copyright (C) 2002-17, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")
 
=== START OF INFORMATION SECTION ===
Device Model:     SSD 240GB
Serial Number:    2019031200647
Firmware Version: R0424D0
User Capacity:    240,057,409,536 bytes [240 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 T13/2015-D revision 3
SATA Version is:  SATA 3.2, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Mon May  6 09:05:50 2019 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
 
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
No failed Attributes found.
 
General SMART Values:
Offline data collection status:  (0x02)    Offline data collection activity was completed without error. Auto Offline Data Collection: Disabled.

Self-test execution status:      (   0)    The previous self-test routine completed without error or no self-test has ever been run.
Total time to complete Offline data collection:         (  120) seconds.

Offline data collectioncapabilities:              (0x11) SMART execute Offline immediate. No Auto Offline data collection support.  Suspend Offline collection upon new                    command.                    No Offline surface scan supported.                    Self-test supported.                    No Conveyance Self-test supported.                    No Selective Self-test supported.

SMART capabilities:            (0x0002)    Does not save SMART data before                    entering power-saving mode.                    Supports SMART auto save timer.

Error logging capability:        (0x01)    Error logging supported.                    General Purpose Logging supported.
Short self-test routine recommended polling time:      (   2) minutes.
Extended self-test routinerecommended polling time:      (  10) minutes.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE  
1 Raw_Read_Error_Rate     0x0032   100   100   050    Old_age   Always       -       0  
5 Reallocated_Sector_Ct   0x0032   100   100   050    Old_age   Always       -       0  
9 Power_On_Hours          0x0032   100   100   050    Old_age   Always       -       135 
12 Power_Cycle_Count       0x0032   100   100   050    Old_age   Always       -       34
160 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       0
161 Unknown_Attribute       0x0033   100   100   050    Pre-fail  Always       -       100
163 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       25
164 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       843
165 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       6
166 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       1
167 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       2
168 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       7000
169 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       100
175 Program_Fail_Count_Chip 0x0032   100   100   050    Old_age   Always       -       0
176 Erase_Fail_Count_Chip   0x0032   100   100   050    Old_age   Always       -       0
177 Wear_Leveling_Count     0x0032   100   100   050    Old_age   Always       -       0
178 Used_Rsvd_Blk_Cnt_Chip  0x0032   100   100   050    Old_age   Always       -       0
181 Program_Fail_Cnt_Total  0x0032   100   100   050    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   100   100   050    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   050    Old_age   Always       -       26
194 Temperature_Celsius     0x0022   100   100   050    Old_age   Always       -       45
195 Hardware_ECC_Recovered  0x0032   100   100   050    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   100   100   050    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   050    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0032   100   100   050    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x0032   100   100   050    Old_age   Always       -       0
232 Available_Reservd_Space 0x0032   100   100   050    Old_age   Always       -       100
241 Total_LBAs_Written      0x0030   100   100   050    Old_age   Offline      -       6436
242 Total_LBAs_Read         0x0030   100   100   050    Old_age   Offline      -       10046
245 Unknown_Attribute       0x0032   100   100   050    Old_age   Always       -       8288

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]

Selective Self-tests/Logging not supported

```

---

