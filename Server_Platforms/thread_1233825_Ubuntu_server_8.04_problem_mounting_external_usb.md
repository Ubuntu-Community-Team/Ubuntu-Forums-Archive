---
title: "Ubuntu server 8.04 problem mounting external usb"
date: 2009-08-07
forum: Server Platforms
---

### Post by payton on 2009-08-07
We had a crash some time ago and had to rescue the /etc folder from a backup. The server is now working fine except for that I cannot seem to mount the USB external backup disc. I mount it using the same command as before the crash:
```
sudo mount /dev/sdd1 /mnt/usb
```

Problem is that now what is shown in /mnt/usb is exactly the same as in /data/. One could think that the /dev/sdd1/ was already mounted in /data, and indeed this seems to be the case. Output from the mount command before mounting the usb is:
```

/dev/sda3 on / type xfs (rw,relatime)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda2 on /boot type ext3 (rw,relatime)
/dev/sdd1 on /data type xfs (rw,relatime)
/dev/sda7 on /srv type xfs (rw,relatime)
/dev/sda6 on /var type xfs (rw,relatime)
/dev/sdb1 on /vault type xfs (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)

```

As you can see the it says /dev/sdd1 is already mounted. This is not the original setup as the disc mounted to /data is a regular internal disc.

My fstab file is as follows:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=3ba82617-133a-4b3e-93a5-984e7c5f3f94 /               xfs     relatime        0       1
# /dev/sda2
UUID=e19e9520-ed3b-4ca8-bc56-e0b6be14ebd3 /boot           ext3    relatime        0       2
# /dev/sdc1
UUID=368016ef-55be-45fe-9ce2-89d7a7a62fcc /data           xfs     relatime        0       2
# /dev/sda7
UUID=6e015326-2127-47a4-ada4-63297e99765f /srv            xfs     relatime        0       2
# /dev/sda6
UUID=d177c321-daa6-4899-98b6-e46785e49eaf /var            xfs     relatime        0       2
# /dev/sdb1
UUID=a5089acb-aaac-459e-9519-7d4277e62843 /vault          xfs     relatime        0       2
# /dev/sda5
UUID=1384b0c8-e799-4355-a534-70463a731133 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
:

```


As you see it is supposedly /dev/sdc1 that is mounted to /data. How can it have happened that now what used to be sdc1 now is sdd1 (most probably something I did :) )?

Any clues on how to resolve the situation would be much appreciated.

Regards.

---

