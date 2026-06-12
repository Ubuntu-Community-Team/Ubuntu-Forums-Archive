---
title: "fstab issue?"
date: 2015-11-16
forum: Server Platforms
---

### Post by DaveCave on 2015-11-16
[ATTACH=CONFIG]265627[/ATTACH]

Can anyone inform me how to rectify this issue?

---

### Post by DaveCave on 2015-11-16
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=a58810e1-7f1b-439e-b787-5086ce96d848 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=da68c1bd-597e-4336-8b90-fa11eeda8185 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//192.168.1.177/d$/Documents/Larry/      /media/Larry   cifs      user,gid=33,uid=33,credentials=/home/david/.smbcredentials  0     0
//192.168.1.177/d$/Documents/David/        /media/David   cifs    user,gid=33,uid=33,credentials=/home/david/.smbcredentials      0       0
//192.168.1.177/d$/Documents/Jackie/        /media/Jackie  cifs    user,gid=33,uid=33,credentials=/home/david/.smbcredentials      0       0
```

---

### Post by darkod on 2015-11-18
Do you still need help with this?

The errors in the screenshot mention /dev/sda2. What is /dev/sda2?

From fstab swap seems to be /dev/sda5 and I assume root is /dev/sda1. So what is sda2? The extended partition where sda5 is located?

---

