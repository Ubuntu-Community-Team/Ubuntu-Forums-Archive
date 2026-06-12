---
title: "Gangling HD drives – strange behavior after installing second HD"
date: 2008-06-28
forum: Server Platforms
---

### Post by volmark on 2008-06-28
I have installed second HD drive, created file system with &#8220;mkfs -t ext3 /dev/sdb1&#8221; and mounted first manually and then remounted after editing of fstab. All went fine.
Unfortunately after rebooting my HD drives were mutually changed: primary HD drive that was /dev/sda1 became /div/sdb1 (and respectively other logical drives) and /dev/sdb1 became /dev/sda1.
Strange &#8230;

This is my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1010ffdb-c0fb-4f1d-9e65-589160c3bcd8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=dd32c617-6437-42ce-b3dc-17a9977fa74c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# 2. HD
/dev/sdb1       /media/hd2      ext3    defaults        0       0

---

### Post by windependence on 2008-06-28
See this post:

[http://ubuntuforums.org/showthread.php?t=836542](http://ubuntuforums.org/showthread.php?t=836542)


-Tim

---

