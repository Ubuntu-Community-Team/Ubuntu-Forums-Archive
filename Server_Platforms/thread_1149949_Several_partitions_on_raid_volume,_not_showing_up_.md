---
title: "Several partitions on raid volume, not showing up in /dev/disk/by-uuid"
date: 2009-05-05
forum: Server Platforms
---

### Post by bdeclerc on 2009-05-05
I've got three drives in my system, one non-raided for the boot volume, two bigger drives in a mirrored software raid.

On the raid volume, /dev/md0, I've got two partitions /dev/md0p1 & /dev/md0p2

In /dev/disk/by-uuid/ only the /dev/md0 device shows up, so I can't add the two partitions themselves into the fstab for mounting at boot on UUID.

When I do 

vol_id --uuid /dev/md0p1

on the command line, I do get a UUID, but when I configure this in /etc/fstab, the system complains that the "special device" does not exist.

Any suggestions on how to get the system to see the UUID's for the two partitions correctly?

---

