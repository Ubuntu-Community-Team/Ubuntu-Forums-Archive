---
title: "ACL not working on LVM paritions"
date: 2012-07-19
forum: Server Platforms
---

### Post by adalal on 2012-07-19
Hey,
I recently reinstalled my server, and provisioned for LVMs, and it's working.. mostly.

My fstab are as follows:
```

aritra@adalal:~$ cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda2       /       ext4    errors=remount-ro,relatime,acl  0       1
/dev/sda1       /boot   ext4    errors=remount-ro,relatime      0       1
/dev/sda3       swap    swap    defaults        0       0
proc            /proc   proc    defaults                0       0
sysfs           /sys    sysfs   defaults                0       0
dev             /dev    devtmpfs        rw      0       0
/dev/vg/backup  /backup ext4    noauto  0       0
/dev/vg/log     /var/log        ext4    defaults        0       0
/dev/vg/home    /home   ext4    suid,dev        0       2
/dev/vg/media   /media  ext4    errors=remount-ro,acl   0       0
/dev/vg/websites        /websites       ext4    suid,errors=remount-ro,dev,acl,noatime  0       2
/dev/vg/progs   /opt    ext4    suid,errors=remount-ro,dev,acl  0       0

```

And here is my mtab...
```

aritra@adalal:~$ cat /etc/mtab
rootfs / rootfs rw 0 0
/dev/root / ext4 rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev /dev devtmpfs rw,relatime,size=8163580k,nr_inodes=2040895,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620 0 0
none /run tmpfs rw,nosuid,noexec,relatime,size=1632780k,mode=755 0 0
none /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
none /run/shm tmpfs rw,nosuid,nodev,relatime 0 0
/dev/sda1 /boot ext4 rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered 0 0
/dev/mapper/vg-log /var/log ext4 rw,relatime,user_xattr,barrier=1,data=ordered 0 0
/dev/mapper/vg-progs /opt ext4 rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered 0 0
/dev/mapper/vg-home /home ext4 rw,relatime,user_xattr,barrier=1,data=ordered 0 0
/dev/mapper/vg-media /media ext4 rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered 0 0
/dev/mapper/vg-websites /websites ext4 rw,noatime,errors=remount-ro,user_xattr,barrier=1,data=ordered 0 0

```

For some reason, the ACL options will not actually load on the LVM mounts.

Any ideas why?

---

### Post by adalal on 2012-07-19
Nevermind, sorry about that... figured out what went wrong...

---

