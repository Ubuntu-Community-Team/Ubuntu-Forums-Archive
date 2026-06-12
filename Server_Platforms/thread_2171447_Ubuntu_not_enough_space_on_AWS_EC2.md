---
title: "Ubuntu not enough space on AWS EC2"
date: 2013-08-30
forum: Server Platforms
---

### Post by bojloc on 2013-08-30
I have 25GB volume on EC2. OS is Ubuntu 12.04 LTS. I can connect to it, but cannot even write 1KB. I tried to delete some files and write again - the same result - not enough space.


I tried to check free space and got this error.


    df -h
    df: cannot read table of mounted file systems: No such file or directory


Then I tried to get directory sizes. It seems that only 13GB from 25GB is full:


    du -h --max-depth=1
    18M     ./boot
    16K     ./lost+found
    4.0K    ./tmp
    83M     ./lib
    192K    ./home
    8.7M    ./bin
    4.0K    ./selinux
    4.0K    ./opt
    100K    ./root
    8.0K    ./dev
    du: cannot access `./proc/1312/task/1312/fd/4': No such file or directory
    du: cannot access `./proc/1312/task/1312/fdinfo/4': No such file or directory
    du: cannot access `./proc/1312/fd/4': No such file or directory
    du: cannot access `./proc/1312/fdinfo/4': No such file or directory
    0       ./proc
    7.9M    ./sbin
    434M    ./usr
    172K    ./run
    13G     ./var
    0       ./sys
    4.0K    ./srv
    4.0K    ./mnt
    4.0K    ./lib64
    4.0K    ./media
    5.8M    ./etc
    13G     .


Mounts


    mount
    sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
    proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
    udev on /dev type devtmpfs (rw,relatime,size=1912272k,nr_inodes=478068,mode=755)
    devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
    tmpfs on /run type tmpfs (rw,nosuid,relatime,size=768100k,mode=755)
    /dev/disk/by-label/cloudimg-rootfs on / type ext4 (rw,relatime,user_xattr,acl,barrier=1,data=ordered)
    none on /sys/fs/fuse/connections type fusectl (rw,relatime)
    none on /sys/kernel/debug type debugfs (rw,relatime)
    none on /sys/kernel/security type securityfs (rw,relatime)
    none on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
    none on /run/shm type tmpfs (rw,nosuid,nodev,relatime)


How can I solve this problem?

---

### Post by houstonbofh on 2013-08-30
I think you are missing a key part...
> lee@dev01:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)

Note how in yours / is not mounted...  Do you have a full system, or the Amazon static Ubuntu you can't really modify?

---

### Post by sandyd on 2013-08-30
> **bojloc said:**
> [B]I have 25GB volume on EC2. OS is Ubuntu 12.04 LTS. I can connect to it, but cannot even write 1KB. I tried to delete some files and write again - the same result - not enough space.


I tried to check free space and got this error.


    df -h
    df: cannot read table of mounted file systems: No such file or directory


Then I tried to get directory sizes. It seems that only 13GB from 25GB is full:


    du -h --max-depth=1
    18M     ./boot
    16K     ./lost+found
    4.0K    ./tmp
    83M     ./lib
    192K    ./home
    8.7M    ./bin
    4.0K    ./selinux
    4.0K    ./opt
    100K    ./root
    8.0K    ./dev
    du: cannot access `./proc/1312/task/1312/fd/4': No such file or directory
    du: cannot access `./proc/1312/task/1312/fdinfo/4': No such file or directory
    du: cannot access `./proc/1312/fd/4': No such file or directory
    du: cannot access `./proc/1312/fdinfo/4': No such file or directory
    0       ./proc
    7.9M    ./sbin
    434M    ./usr
    172K    ./run
    13G     ./var
    0       ./sys
    4.0K    ./srv
    4.0K    ./mnt
    4.0K    ./lib64
    4.0K    ./media
    5.8M    ./etc
    13G     .


Mounts


    mount
    sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
    proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
    udev on /dev type devtmpfs (rw,relatime,size=1912272k,nr_inodes=478068,mode=755)
    devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
    tmpfs on /run type tmpfs (rw,nosuid,relatime,size=768100k,mode=755)
    /dev/disk/by-label/cloudimg-rootfs on / type ext4 (rw,relatime,user_xattr,acl,barrier=1,data=ordered)
    none on /sys/fs/fuse/connections type fusectl (rw,relatime)
    none on /sys/kernel/debug type debugfs (rw,relatime)
    none on /sys/kernel/security type securityfs (rw,relatime)
    none on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
    none on /run/shm type tmpfs (rw,nosuid,nodev,relatime)


How can I solve this problem?


[/B]
When setting up the instance you should have a screen like below - make sure youve selected the volumes properly
[ATTACH=CONFIG]245851[/ATTACH]

df -h should look like
[ATTACH=CONFIG]245852[/ATTACH]

---

### Post by bojloc on 2013-08-31
Here is 2 screenshots from EC2 control panel

[http://clip2net.com/s/5FcLVi](http://clip2net.com/s/5FcLVi)
[http://clip2net.com/s/5FcNmA](http://clip2net.com/s/5FcNmA)

---

### Post by bojloc on 2013-08-31
[COLOR=#444444][FONT=Arial]cat /etc/mtab cat: /etc/mtab: No such file or directory

[/FONT][/COLOR]cat /etc/fstab
LABEL=cloudimg-rootfs   /        ext4   defaults        0 0

---

### Post by bojloc on 2013-08-31
> **houstonbofh said:**
> I think you are missing a key part...


Note how in yours / is not mounted...  Do you have a full system, or the Amazon static Ubuntu you can't really modify?


How can I mount it? I can modify this instance.

---

### Post by houstonbofh on 2013-08-31
The key part missing is your root directory, but in the system and in the fstab.  This is a major issue...  I would start with a reboot and see if the root is found again.

---

### Post by bojloc on 2013-08-31
I tried to reboot - nothing happens

---

### Post by Habitual on 2013-08-31
[http://alestic.com/2010/02/ec2-resize-running-ebs-root](http://alestic.com/2010/02/ec2-resize-running-ebs-root)

---

### Post by bojloc on 2013-09-01
There are enough space on root - 25GB. And only 13GB are used. But I cannot write anything.

---

### Post by sandyd on 2013-09-05
does
```

mount /
``` output anything?

If you run
```

fdisk -l
```
it should output something like
```

fdisk -l

Disk /dev/xvda1: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/xvda1 doesn't contain a valid partition table
```

---

### Post by Kashyap01 on 2013-09-11
try below command and find if you can kill process related to that files,It could be possible that some process are still using tmp files which already deleted,Try to identify which process causing that & try to kill that process first.
Possibly it could be because of infinite loop process or process that running from long time.

```
lsof | grep deleted
```

---

