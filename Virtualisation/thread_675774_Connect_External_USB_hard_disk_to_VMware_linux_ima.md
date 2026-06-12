---
title: "Connect External USB hard disk to VMware linux image"
date: 2008-01-23
forum: Virtualisation
---

### Post by andreh on 2008-01-23
Hello,
Is it possible to connect an external usb hard disk to an linux VMWare image ?
Or is it nog possible to do this ?
I want to read my NTFS external HD data from my VMWAre linux.

---

### Post by andreh on 2008-01-23
> user@ubuntu:~$ **uname -a**
Linux ubuntu 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
user@ubuntu:~$
> user@ubuntu:~$ [b]df -h 
Filesystem            Size  Used Avail Use% Mounted on[/b]
/dev/loop7            5,8G  2,3G  3,3G  41% /
varrun               1013M  104K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
procbususb           1013M  144K 1013M   1% /proc/bus/usb
udev                 1013M  144K 1013M   1% /dev
devshm               1013M     0 1013M   0% /dev/shm
lrm                  1013M   33M  981M   4% /lib/modules/2.6.20-16-generic/volatile
/dev/loop6            2,0G  139M  1,7G   8% /home
/dev/sdb1             150G   21G  130G  14% /media/LaCie

user@ubuntu:~$
> user@ubuntu:~$ [b]  cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/b] 
proc            /proc           proc        defaults    0   0
/dev/loop7      /               ext3        defaults    0   1
/dev/loop6      /home           ext3        defaults    0   2
/dev/loop5      none            swap        sw          0   0
/dev/loop4      /media/extra    auto        defaults    0   0

user@ubuntu:~$
> [b]
user@ubuntu:~$ dmesg | grep sd
[/b]

't support DPO or FUA
[    6.163239] SCSI device sda: 78140160 512-byte hdwr sectors (40008 MB)
[    6.163248] sda: Write Protect is off
[    6.163250] sda: Mode Sense: 00 3a 00 00
[    6.163265] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.163268]  sda: sda1
[    6.238064] sd 0:0:0:0: Attached scsi disk sda
[    7.604000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   69.092000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[   69.092000] sdb: Write Protect is off
[   69.092000] sdb: Mode Sense: 00 38 00 00
[   69.092000] sdb: assuming drive cache: write through
[   69.096000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[   69.096000] sdb: Write Protect is off
[   69.096000] sdb: Mode Sense: 00 38 00 00
[   69.096000] sdb: assuming drive cache: write through
[   69.096000]  sdb: sdb1
[   69.104000] sd 2:0:0:0: Attached scsi disk sdb
[   69.104000] sd 2:0:0:0: Attached scsi generic sg2 type 0
user@ubuntu:~$
En hier nog wat meer info:
> user@ubuntu:~$** cat /etc/mtab**
/dev/loop7 / ext3 rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
/dev/loop6 /home ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0[b]
/dev/sdb1 /media/LaCie vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0
[/b]
user@ubuntu:~$
en de schijf zelf

> user@ubuntu:~$** fdisk -l**

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  [b]
 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    b  W95 FAT32
[/b]
user@ubuntu:~$

---

