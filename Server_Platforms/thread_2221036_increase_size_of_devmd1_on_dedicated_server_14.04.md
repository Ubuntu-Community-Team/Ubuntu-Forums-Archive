---
title: "increase size of /dev/md1 on dedicated server 14.04"
date: 2014-04-30
forum: Server Platforms
---

### Post by semicolon2 on 2014-04-30
Dear ALL,

I am new to ubuntu server .I just purchased a ubuntu dedicated server 14.04. But the problem is /dev/md1 is mounted on / and /dev/md1 is of 4gb. I need bigger space for / and /opt. Help me in doing this. I am pasting some output.

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sdb1[1] sda1[0]
      4194240 blocks [2/2] [UU]


md3 : active raid1 sda3[0] sdb3[1]
      1947222016 blocks [2/2] [UU]


unused devices: <none>

------------------------
Filesystem             Size  Used Avail Use% Mounted on
/dev/md1               4.0G  561M  3.4G  15% /
none                   4.0K     0  4.0K   0% /sys/fs/cgroup
udev                    16G  4.0K   16G   1% /dev
tmpfs                  3.2G  728K  3.2G   1% /run
none                   5.0M     0  5.0M   0% /run/lock
none                    16G     0   16G   0% /run/shm
none                   100M     0  100M   0% /run/user
/dev/mapper/vg00-var    54G  399M   51G   1% /var
/dev/mapper/vg00-usr    54G  629M   51G   2% /usr
/dev/mapper/vg00-home   54G   13M   51G   1% /home


--------------
fdisk -l


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf318795a


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     8390655     4194304   fd  Linux raid autodetect
/dev/sda2         8390656    12584959     2097152   82  Linux swap / Solaris
/dev/sda3        12584960  3907029167  1947222104   fd  Linux raid autodetect


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x58d81426


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     8390655     4194304   fd  Linux raid autodetect
/dev/sdb2         8390656    12584959     2097152   82  Linux swap / Solaris
/dev/sdb3        12584960  3907029167  1947222104   fd  Linux raid autodetect


Disk /dev/md3: 1994.0 GB, 1993955344384 bytes
2 heads, 4 sectors/track, 486805504 cylinders, total 3894444032 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/md3 doesn't contain a valid partition table


Disk /dev/md1: 4294 MB, 4294901760 bytes
2 heads, 4 sectors/track, 1048560 cylinders, total 8388480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/md1 doesn't contain a valid partition table


Disk /dev/mapper/vg00-usr: 58.0 GB, 57982058496 bytes
255 heads, 63 sectors/track, 7049 cylinders, total 113246208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/vg00-usr doesn't contain a valid partition table


Disk /dev/mapper/vg00-var: 58.0 GB, 57982058496 bytes
255 heads, 63 sectors/track, 7049 cylinders, total 113246208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/vg00-var doesn't contain a valid partition table


Disk /dev/mapper/vg00-home: 58.0 GB, 57982058496 bytes
255 heads, 63 sectors/track, 7049 cylinders, total 113246208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/vg00-home doesn't contain a valid partition table
---------------------------------------
NAME                   MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                      8:0    0   1.8T  0 disk
&#9500;&#9472;sda1                   8:1    0     4G  0 part
&#9474; &#9492;&#9472;md1                  9:1    0     4G  0 raid1 /
&#9500;&#9472;sda2                   8:2    0     2G  0 part  [SWAP]
&#9492;&#9472;sda3                   8:3    0   1.8T  0 part
  &#9492;&#9472;md3                  9:3    0   1.8T  0 raid1
    &#9500;&#9472;vg00-usr (dm-0)  252:0    0    54G  0 lvm   /usr
    &#9500;&#9472;vg00-var (dm-1)  252:1    0    54G  0 lvm   /var
    &#9492;&#9472;vg00-home (dm-2) 252:2    0    54G  0 lvm   /home
sdb                      8:16   0   1.8T  0 disk
&#9500;&#9472;sdb1                   8:17   0     4G  0 part
&#9474; &#9492;&#9472;md1                  9:1    0     4G  0 raid1 /
&#9500;&#9472;sdb2                   8:18   0     2G  0 part  [SWAP]
&#9492;&#9472;sdb3                   8:19   0   1.8T  0 part
  &#9492;&#9472;md3                  9:3    0   1.8T  0 raid1
    &#9500;&#9472;vg00-usr (dm-0)  252:0    0    54G  0 lvm   /usr
    &#9500;&#9472;vg00-var (dm-1)  252:1    0    54G  0 lvm   /var
    &#9492;&#9472;vg00-home (dm-2) 252:2    0    54G  0 lvm   /home

--------------------------------------------------



 --- Physical volume ---
  PV Name               /dev/md3
  VG Name               vg00
  PV Size               1.81 TiB / not usable 4.00 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              475395
  Free PE               433923
  Allocated PE          41472
  PV UUID               3JBAif-3jv8-cyL2-boQc-d3OP-zYBV-WKiFrG
---------------------------

---

### Post by nerdtron on 2014-04-30
You may increase the LVM partitions but I don't think you can increase raid partitions such as /dev/md1.

---

### Post by semicolon2 on 2014-04-30
yes i did increase lvm partition but stuck on /dev/md1 raid1 type. Any suggestion?

---

### Post by steeldriver on 2014-04-30
I think the question I'd be asking is why does / need more size if /usr, /var and /home are elsewhere (md3)? That only really leaves /boot, /etc, and possibly /opt.

If you use a lot of space in /opt, perhaps a better solution would be to create a separate LV for that alongside your /usr, /var, /home volumes?

OTOH if you have 4G of old kernels in /boot and other cruft, a good cleanup may be all that's required.

---

### Post by semicolon2 on 2014-04-30
Thanks you for your reply.Because I want to install xampp and xampp installs in /opt and application running on xampp will be needing lot of space. Any other way around? .

---

### Post by semicolon2 on 2014-04-30
> **steeldriver said:**
> I think the question I'd be asking is why does / need more size if /usr, /var and /home are elsewhere (md3)? That only really leaves /boot, /etc, and possibly /opt.

If you use a lot of space in /opt, perhaps a better solution would be to create a separate LV for that alongside your /usr, /var, /home volumes?

OTOH if you have 4G of old kernels in /boot and other cruft, a good cleanup may be all that's required.


----------------
What I need to learn to create separate LV for /opt?. Thank you

---

