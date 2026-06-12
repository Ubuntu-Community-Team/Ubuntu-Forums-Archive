---
title: "Problem auto mounting eSATA drive on pnp"
date: 2009-09-25
forum: Server Platforms
---

### Post by Scottie_ on 2009-09-25
The problem i'm having is with 9.04 after boot the drive will not auto mount/umount when i connect/disconnect it, but the device nodes are created.

The only way it will mount currently is either if the drive is connected at boot time, or if i mount it manually (ie: mount -a or mount /dev/sd...).

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c33a5902-73bb-4e78-a553-dd96c9041c74 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=410bb754-d2e0-4427-838d-3de783d7c465 none            swap    sw              0       0
# /dev/md0
UUID=8853f829-91b9-4609-8ae2-cc93df91860b /media/md0      ext3    defaults 0       0
# /dev/scd0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# eSATA Backup
UUID=967c5f7e-595b-48f7-a0bf-82e5cfa50b75 /media/external ext3    auto,users 0 0

```I've looked around, tried numerious things people have suggested to others and nothing has fixed it.

---

