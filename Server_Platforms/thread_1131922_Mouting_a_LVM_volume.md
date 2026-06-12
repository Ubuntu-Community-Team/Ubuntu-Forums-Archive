---
title: "Mouting a LVM volume?"
date: 2009-04-21
forum: Server Platforms
---

### Post by submute on 2009-04-21
Totally confused here, after following this- [https://help.ubuntu.com/community/Installation/FileServerWithRAID](https://help.ubuntu.com/community/Installation/FileServerWithRAID)

Basically I can't figure out how to mount the logical volume. After running lvcreate, lvscan reports:

```
root@felix:~# lvscan
ACTIVE            '/dev/raid/bigfish' [1.65 TB] inherit

```

Also, pvdisplay reports:
```
  --- Physical volume ---
  PV Name               /dev/md2
  VG Name               raid
  PV Size               1.65 TB / not usable 1.00 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              432731
  Free PE               0
  Allocated PE          432731
  PV UUID               rsan2T-uYnL-e6g6-te7G-yghV-cGh1-rou1Jo
```

But, df -H just reports:
```
root@felix:~# df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/md0                30G   684M    28G   3% /
tmpfs                  2.1G      0   2.1G   0% /lib/init/rw
varrun                 2.1G    54k   2.1G   1% /var/run
varlock                2.1G      0   2.1G   0% /var/lock
udev                   2.1G   3.0M   2.1G   1% /dev
tmpfs                  2.1G      0   2.1G   0% /dev/shm
```

How do I get this newly created LVM volume mounted as a drive? Thanks much!

---

### Post by Brazen on 2009-04-21
> **submute said:**
> Totally confused here, after following this- [https://help.ubuntu.com/community/Installation/FileServerWithRAID](https://help.ubuntu.com/community/Installation/FileServerWithRAID)

Basically I can't figure out how to mount the logical volume. After running lvcreate, lvscan reports:

```
root@felix:~# lvscan
ACTIVE            '/dev/raid/bigfish' [1.65 TB] inherit

```

<snip>

How do I get this newly created LVM volume mounted as a drive? Thanks much!

First you need to create a file system on it.  You can do that with this:
```

sudo mkfs.xfs /dev/mapper/raid-bigfish

```

And then you can mount it.  You can replace 'mkfs.xfs' with 'mkfs.ext3' if you want to use ext3 filesystem instead of xfs filesystem.  You need to make sure the mount location exists.  Say you want to mount it at '/mnt/bigfish' then you would do this:
```

sudo mkdir /mnt/bigfish
sudo mount /dev/mapper/raid-bigfish /mnt/bigfish

```

For the mount to reappear, you'll need to add an entry for it in /etc/fstab.

---

### Post by submute on 2009-04-21
Perfect... much obliged!

---

