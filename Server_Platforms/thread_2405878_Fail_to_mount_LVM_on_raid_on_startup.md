---
title: "Fail to mount LVM on raid on startup"
date: 2018-11-12
forum: Server Platforms
---

### Post by raversnet2 on 2018-11-12
I've been unable to mount my LVs on boot that reside on a High Point controller.  Normally the boot hangs at mounting of the LV and times out. 

 I then need to drop to shell and remove the entry:

UUID=MMDEva-uBpn-yE7l-cRuG-3hOH-Hcm9-XJQ5Li /mnt/OPT    ext4    defaults    1 2

 from /etc/fstab. 

 Once the boot continues, the formatted LV

**Auto mounts to /media/rob/OPT on /dev/dm-3 **** ******Every-time***

 Ubuntu boots from a separate SSD that is not on a LVM just a standard partition.

My System:

Linux ubuntu 4.15.0-38-generic #41-Ubuntu SMP Wed Oct 10 10:59:38 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
High Point Raid SSD7101A-1

```
# cat /etc/fstab                                                                                                                                            [12:48:04]
UUID=68e43f21-defd-11e8-bb6b-509a4c948bb2 / ext4 defaults 0 0
UUID=85C4-45E7 /boot/efi vfat defaults 0 0
/swap.img    none    swap    sw    0    0

UUID=MMDEva-uBpn-yE7l-cRuG-3hOH-Hcm9-XJQ5Li /mnt/OPT    ext4    defaults    1 2



```

```
LVDisplay

 --- Logical volume ---
  LV Path                /dev/ubuntu/OPT
  LV Name                OPT
  VG Name                ubuntu
  LV UUID                MMDEva-uBpn-yE7l-cRuG-3hOH-Hcm9-XJQ5Li
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2018-11-06 13:09:03 -0600
  LV Status              available
  # open                 0
  LV Size                100.00 GiB
  Current LE             25600
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:3

```

```
Journalctl -xb

Nov 12 11:29:25 ubuntu systemd[1]: Found device THNSF8120CCSE 
Subject: Unit dev-disk-by\x2duuid-85C4\x2d45E7.device has finished start-up
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit dev-disk-by\x2duuid-85C4\x2d45E7.device has finished starting up.
-- 
-- The start-up result is RESULT.
Nov 12 11:29:25 ubuntu systemd[1]: Mounting /boot/efi...
-- Subject: Unit boot-efi.mount has begun start-up
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit boot-efi.mount has begun starting up.
Nov 12 11:29:25 ubuntu systemd[1]: Mounted /boot/efi.
-- Subject: Unit boot-efi.mount has finished start-up
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit boot-efi.mount has finished starting up.
-- 
-- The start-up result is RESULT.
Nov 12 11:30:53 ubuntu systemd[1]: dev-disk-by\x2duuid-MMDEva\x2duBpn\x2dyE7l\x2dcRuG\x2d3hOH\x2dHcm9\x2dXJQ5Li.device: Job dev-disk-by\x2duuid-MMDEva\x2duBpn\x2dyE7l\x2dcRuG\
Nov 12 11:30:53 ubuntu systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-MMDEva\x2duBpn\x2dyE7l\x2dcRuG\x2d3hOH\x2dHcm9\x2dXJQ5Li.device.
-- Subject: Unit dev-disk-by\x2duuid-MMDEva\x2duBpn\x2dyE7l\x2dcRuG\x2d3hOH\x2dHcm9\x2dXJQ5Li.device has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit dev-disk-by\x2duuid-MMDEva\x2duBpn\x2dyE7l\x2dcRuG\x2d3hOH\x2dHcm9\x2dXJQ5Li.device has failed.
-- 
-- The result is RESULT.
Nov 12 11:30:53 ubuntu systemd[1]: Dependency failed for File System Check on /dev/disk/by-uuid/MMDEva-uBpn-yE7l-cRuG-3hOH-Hcm9-XJQ5Li.
-- Subject: Unit systemd-fsck@dev-disk-by\x2duuid-MMDEva\x2duBpn\x2dyE7l\x2dcRuG\x2d3hOH\x2dHcm9\x2dXJQ5Li.service has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit systemd-fsck@dev-disk-by\x2duuid-MMDEva\x2duBpn\x2dyE7l\x2dcRuG\x2d3hOH\x2dHcm9\x2dXJQ5Li.service has failed.
-- 
-- The result is RESULT.
Nov 12 11:30:53 ubuntu systemd[1]: Dependency failed for /mnt/OPT.
-- Subject: Unit mnt-OPT.mount has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit mnt-OPT.mount has failed.
-- 
-- The result is RESULT.
Nov 12 11:30:53 ubuntu systemd[1]: Dependency failed for Local File Systems.
-- Subject: Unit local-fs.target has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit local-fs.target has failed.
-- 
-- The result is RESULT.
```


I can mount manually using a variety of combinations. 

 ex:  **mount /dev/dm-3 /mnt/OPT**   or   **mount /dev/mapper/ubuntu-OPT /mnt/OPT**  or  [B]mount /dev/ubuntu/OPT /mnt/OPT

[/B]They are all successful.  

Systemd is reporting a failed dependency so i'm guessing a service is not yet started that will allow me to mount the LV on boot.

---

### Post by raversnet2 on 2018-11-12
Rebooted again and when the system failed to boot and dropped to the command line I ran a few more tests.

[B]~/blkid (shows the raid controller showing up)
[/B]

```
/dev/hptblock0n0p1: UUID="7cBdmu-Qh2p-Oljj-c5C2-GeQ0-YzDT-TRXeMc" TYPE="LVM2_member" PARTLABEL="LVM" PARTUUID="27e613ae-0989-4457-ba3a-04c3b7294529"
/dev/sda1: UUID="85C4-45E7" TYPE="vfat" PARTUUID="b21035c6-4227-4f71-b3b8-f780812d24f1"
/dev/sda2: UUID="68e43f21-defd-11e8-bb6b-509a4c948bb2" TYPE="ext4" PARTUUID="9b4e0311-4887-4d0b-998d-e79304172f54"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/hptblock0n0: PTUUID="2332ad3c-778e-4411-bbc7-0748046688c9" PTTYPE="gpt"

```
[B]~/lvdisplay (LVs are visible)
[/B]```

--- Logical volume ---
LV Path /dev/ubuntu/TBW
LV Name TBW
VG Name ubuntu
LV UUID ytjVfW-Fp67-zZ1k-gPHG-5MIS-iIlj-1TumRo
LV Write Access read/write
LV Creation host, time ubuntu, 2018-11-05 17:15:45 -0600
LV Status NOT available
LV Size 100.00 GiB
Current LE 25600
Segments 1
Allocation inherit
Read ahead sectors auto
   
--- Logical volume ---
LV Path /dev/ubuntu/EDOCS
LV Name EDOCS
VG Name ubuntu
LV UUID mTtYrs-BejP-m74j-Uvko-aMT9-ClBN-IvpU6O
LV Write Access read/write
LV Creation host, time ubuntu, 2018-11-05 17:16:02 -0600
LV Status NOT available
LV Size 100.00 GiB
Current LE 25600
Segments 1
Allocation inherit
Read ahead sectors auto
   
--- Logical volume ---
LV Path /dev/ubuntu/LAFRANCE3
LV Name LAFRANCE3
VG Name ubuntu
LV UUID A62tvi-xzFE-sZd1-QqpL-veOs-bzWU-fi0trW
LV Write Access read/write
LV Creation host, time ubuntu, 2018-11-05 17:16:58 -0600
LV Status NOT available
LV Size 500.00 GiB
Current LE 128000
Segments 1
Allocation inherit
Read ahead sectors auto
   
--- Logical volume ---
LV Path /dev/ubuntu/OPT
LV Name OPT
VG Name ubuntu
LV UUID MMDEva-uBpn-yE7l-cRuG-3hOH-Hcm9-XJQ5Li
LV Write Access read/write
LV Creation host, time ubuntu, 2018-11-06 13:09:03 -0600
LV Status NOT available
LV Size 100.00 GiB
Current LE 25600
Segments 1
Allocation inherit
Read ahead sectors auto
```

**~/mount (main OS ****ssd**** loaded)**

```
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=16416072k,nr_inodes=4104018,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=3289728k,mode=755)
/dev/sda2 on / type ext4 (rw,relatime,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=26,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=18506)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
/var/lib/snapd/snaps/core_5742.snap on /snap/core/5742 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_4917.snap on /snap/core/4917 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/canonical-livepatch_50.snap on /snap/canonical-livepatch/50 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
```

Unable to mount drive by symlink as they don't exist? Or by UUID eventhough I can see it under LVDisplay


```
mount: /mnt/OPT: special device /dev/ubuntu/OPT does not exist.
mount: /mnt/OPT: can't find UUID=MMDEva-uBpn-yE71-cRuG-3h0H-Hcm9-XJQ5Li.

```

I believe the symlinks for the VG and LVs are recreated on each boot in /dev.   Why aren't they being created by the time the Fstab is being ran to map the drives?

---

### Post by raversnet2 on 2018-11-14
This appears to be an ongoing bug [https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/1573982](https://bugs.launchpad.net/ubuntu/+source/lvm2/+bug/1573982)

Although I'm not booting from an LVM it does affect my fstab file that attempts to mount LVMs.  Activating the volume groups when the boot fails allows the system to startup.

---

### Post by slickymaster on 2018-11-14
*Thread moved to **Server Platforms**.*

---

