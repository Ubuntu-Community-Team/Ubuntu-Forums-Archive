---
title: "[SOLVED] Ubuntu won't restart without console intervention"
date: 2008-06-09
forum: Server Platforms
---

### Post by Sporkman on 2008-06-09
I'm running a remote server, and ever since upgrading from ubuntu server 7.10 to ubuntu server 8.04, I've had difficulty rebooting, as it would go dead after I rebooted, requiring on-site tech intervention. I asked in a service ticked what they saw on the console, and they wrote:

> 
I think that after the server was rebooted the system found some error in the hard drive. The console displayed the following message:

A maintenance shell will now be started. Control D will terminate this shell.

According to /var/log/fsck, there indeed was a problem...

Here is my /var/log/fsck:

```

Log of fsck -C -R -A -a 
Sun Jun  8 23:53:09 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: No such file or directory while trying to open /dev/hda1
/dev/hda1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Sun Jun  8 23:53:09 2008
----------------

```

Here is my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3	/               ext3    defaults,errors=remount-ro 0       1
/dev/hda1	/boot           ext3    defaults        0       2
/dev/hda2	none            swap    sw              0       0
#/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Here is the output of mount:

```
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
```

Does anybody have any ideas re what's going on, & how to fix it (remotely)?

---

### Post by gtdaqua on 2008-06-09
The error message talks about a superblock on an 'ext2' filesystem wheras fstab calls to mount as 'ext3' filesystem. Instead of specifically mentioning 'ext3' in fstab, can you specify 'auto' and see wat happens?

---

### Post by bluefrog on 2008-06-09
as /boot is a partition you can unmount while online, try to fix the problem with the e2fsck tool.

If still a problem you can always get rid of it by changing the fstab from 0 2 to 0 0.

---

### Post by Sporkman on 2008-06-09
Thanks very much, guys!

E2fsck was coming up with the same "superblock" error, even when I tried to repair it with "-p", so I changed that entry in fstab from ext3 to auto, and from "0 2" to "0 0" as you suggested, and the subsequent reboot finished problem-free.

Thanks again! :guitar:

---

