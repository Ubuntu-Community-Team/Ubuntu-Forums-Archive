---
title: "Missing Logical Volume"
date: 2010-08-10
forum: Server Platforms
---

### Post by Pyraxic on 2010-08-10
At first, we were getting:
/etc/init.d/mysql[19729]: ERROR: The partition with /var/lib/mysql is  too full!
When we took a look at the df -h, one of the logical volumes were full.  We extended the logical volume using:
lvextend -L30G /dev/VolGroup00/(name)
As the file system needs to be increased, we unmounted the partition  using:
umount -l /dev/VolGroup00/(name)

We can't find the partition anymore. It cannot be mounted because it  gives us the message:
mount: can't find /dev/VolGroup00/(name) in /etc/fstab or /etc/mtab

/etc/fstab already have the partition listed:
# /dev/mapper/VolGroup00-name
UUID=e894252d-fbe3-4441-8595-09d8a3f1965d /               ext3     relatime,errors=remount-ro 0       1

Any LVM command gives the following message:
/proc/mounts: fopen %s failed: No such file or directory
  /proc/devices: fopen failed: No such file or directory
What can be done to recover the lost Logical Volume? Any help is  appreciated.

---

