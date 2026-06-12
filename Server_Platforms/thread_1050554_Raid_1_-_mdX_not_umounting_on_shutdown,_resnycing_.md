---
title: "Raid 1 - mdX not umounting on shutdown, resnycing on reboot."
date: 2009-01-25
forum: Server Platforms
---

### Post by PaulHilux on 2009-01-25
Box:
SUPERMICRO MBD-X7SBL-LN2
q6600
8gb ram
500gb sata x 2


I've installed ubuntu 8.04.1 and 8.04.2 LTS multiples times now resulting in the same error. Through the installion disk I create identical partitions on each drive, then create the mdadm arrays through "configure raid", assign file systems, mount points. The install proceeds fine.

Upon reboot, I see notifications stating particular md partitions are either clean, unclean or need resyncing. Once logged in a sudo mdadm --detail /dev/mdX, or cat /proc/mdstat shows some as clean, some as active, some as resyncing, or some as delayed resyncing.

From here I can execute a shutdown/reboot command. I then receive errors "unable to stop mdX", "umount2: device or resource busy" "mounting X read only". When the system reboots I receive clean/unclean/syncing messages again, though it seems to be random which partitions are effected by which.

I've allowed the drives/partitions to go through the syncing process, a shutdown/reboot results in the same errors after this though.

Thoughts?

edit: also, 64bit versions.

---

### Post by PaulHilux on 2009-01-26
[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/111398](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/111398)
[http://lkml.org/lkml/2006/10/6/233](http://lkml.org/lkml/2006/10/6/233)

My issue seems somewhat similar to these. :(

Any insight to a work around?

---

### Post by PaulHilux on 2009-01-26
hmm, now on shutdown I get:

unmounting local fileystems.....
umount2: device or resource busy
umount: /dev/md5 busy - mounting read only

[OK]

on reboot:
kinit: name_to_dev_t(/dev/md1) = md1(9,1)
kinit: trying to resume from /dev/md1
no resume image detected, normal boot

no resnycing, everything active, consistently...

---

### Post by PaulHilux on 2009-01-27
upgraded to Intrepid Kernel, same issue. /dev/md5 is /var, /dev/md1 is swap

shutdown:
unmounting local fileystems....
umount2: device or resource busy
umount: /dev/md5 busy - remounted read only

[OK]

on reboot:
kinit: name_to_dev_t(/dev/md1) = md1(9,1)
kinit: trying to resume from /dev/md1
no resume image detected, normal boot

no resnycing now, All mdx's are reporting "active". Just these worrying errors. Any insight on the meaning of them? Also, any recommendation for another support resource? Another forum?

---

