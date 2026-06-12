---
title: "Errors on LXC Container Shutdown"
date: 2015-05-31
forum: Virtualisation
---

### Post by gstanden on 2015-05-31
What can I do to get rid of these messages ?  These occur on shutdown from an OEL 6.5 container running on Ubuntu 15.04.

Unmounting file systems:                                   [  OK  ]
umount2: Permission denied
umount: /proc/uptime: block devices not permitted on fs
umount2: Permission denied
umount: /proc/sys/fs/binfmt_misc: block devices not permitted on fs
umount2: Permission denied
umount2: Permission denied
umount: /proc/stat: block devices not permitted on fs
umount2: Permission denied
umount: /proc/meminfo: block devices not permitted on fs
umount2: Permission denied
umount: /proc/diskstats: block devices not permitted on fs
umount2: Permission denied
umount: /proc/cpuinfo: block devices not permitted on fs
umount2: Permission denied
umount: /dev/pts: block devices not permitted on fs
init: Re-executing /sbin/init
mount: you must specify the filesystem type
Halting system...
gstanden@u1504:~$ 

Thanks,

Gilbert

---

