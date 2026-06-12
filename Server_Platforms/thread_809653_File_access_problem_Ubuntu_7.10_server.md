---
title: "File access problem Ubuntu 7.10 server"
date: 2008-05-27
forum: Server Platforms
---

### Post by sDoky on 2008-05-27
Hi guys, I've got a little problem, I want to have chmoded my files on my hdd drives on my server to 777 (I know what it takes, please do not comment this). But when I boot the server it is not 777, I have to manually unmount it, chmod to 777 and remount. What should I do? it is a vfat partition. Is it the umask=007? thanks

my server's fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=68ce90b9-633f-40b4-9caa-32c31201b99d /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
# /dev/sda1
UUID=4701-51CC  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sdb1
UUID=4701-51CE  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/hda5
UUID=022d0921-8a0a-4fa2-b8d9-c89bacfab0fd none            swap    sw              0       0

```

my server's mtab:
```

/dev/hda1 / ext3 rw,errors=remount-ro,usrquota,grpquota 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
/dev/sdb1 /media/sdb1 vfat rw 0 0
/dev/sda1 /media/sda1 vfat rw 0 0

```

---

### Post by cdenley on 2008-05-27
Yes, the permissions for vfat are set with the umask mount option. It sounds like you want to change it to umask=000. The fat filesystem is not capable of storing unix permissions, so any changes you make to permissions on that filesystem cannot be persistent.

---

### Post by sDoky on 2008-05-29
Thanks a lot man, that helped.

> **cdenley said:**
> Yes, the permissions for vfat are set with the umask mount option. It sounds like you want to change it to umask=000. The fat filesystem is not capable of storing unix permissions, so any changes you make to permissions on that filesystem cannot be persistent.

---

