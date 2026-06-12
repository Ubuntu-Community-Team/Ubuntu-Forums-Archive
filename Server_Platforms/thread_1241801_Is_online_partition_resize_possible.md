---
title: "Is online partition resize possible?"
date: 2009-08-16
forum: Server Platforms
---

### Post by Philio on 2009-08-16
I have a couple of servers that have been partitioned wrong, wondering if (to save time) there is a way to resize the partitions while server is online?

There is a 6Gb swap partition, I'm wondering if I could use this to install a temporary OS, chroot, unmount /, resize then remount it?

Any ideas anyone?

---

### Post by Philio on 2009-08-16
Sorted, using debootstrap to install OS on the old swap drive :)

---

