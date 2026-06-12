---
title: "/etc/fstab"
date: 2011-07-26
forum: Server Platforms
---

### Post by mbw290 on 2011-07-26
My /etc/fstab file isn't mounting
'# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=317e21c1-85b6-48ee-be8e-831e1dd68f1f /               ext4   errors=remount-ro,usrquota,grpquota, 0       1
# swap was on /dev/sdb1 during installation
UUID=adbfe828-9fcc-46b3-9fed-f743a9228e7f none            swap    sw              0       0

---

### Post by Bachstelze on 2011-07-26
And what does it do instead of "mounting"?

---

### Post by Morbius1 on 2011-07-26
> UUID=317e21c1-85b6-48ee-be8e-831e1dd68f1f / ext4 errors=remount-ro,usrquota,grpquota, 0 1Aside from usrquota and grpquota probably being ignored you might want to get rid of the last comma after "grpquota" and before the "0 1".

---

### Post by mbw290 on 2011-07-26
I got rid of it and I am still getting the error mountall:Filesystem could not be mounted: /etc/fstab

---

### Post by Elfy on 2011-07-26
[COLOR="Red"]'[/COLOR]# /etc/fstab: static file system information. Try getting rid of the ' at the beginning of line 1.

Secondly are you sure the UUID is correct for the partition?

---

### Post by mbw290 on 2011-07-26
That worked!  I can't believe it was such a simple error!  Thank you so much

---

### Post by Elfy on 2011-07-26
Glad it helped. I'd make sure I made backups of critical files.

---

