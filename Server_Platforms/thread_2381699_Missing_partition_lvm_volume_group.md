---
title: "Missing partition lvm volume group"
date: 2018-01-04
forum: Server Platforms
---

### Post by steff911 on 2018-01-04
Hi there,

we have a virtuel server with 3 disks and ubuntu 16.04 with lvm.
After some error with the virtualization environment we get in trouble with booting the server.

We run into initramfs with error message "Couldn´t find device with uuid"

from initramfs console we can browse an see the device sda, sdb and sdc. On sda and sdb there are partitions.
But on sdc there is no partition and as result the volume group cant build.

is there a way to get the partition back?

Best regards

---

### Post by howefield on 2018-01-04
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2018-01-04
Maybe these pages can help you, but first start only with the parts about detecting the issue. If you are not sure which commands to run to help fix it, ask first...

[http://blog.adamsbros.org/2009/05/30/recover-lvm-volume-groups-and-logical-volumes-without-backups/](http://blog.adamsbros.org/2009/05/30/recover-lvm-volume-groups-and-logical-volumes-without-backups/)
[https://www.novell.com/coolsolutions/appnote/19386.html](https://www.novell.com/coolsolutions/appnote/19386.html)

---

