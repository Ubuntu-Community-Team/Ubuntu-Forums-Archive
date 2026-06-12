---
title: "installing GRUB on multiple disks"
date: 2007-12-11
forum: Server Platforms
---

### Post by lee_connell on 2007-12-11
I know it is necessary to recover from a drive failure in a software RAID1 to have written the MBR to both disks if you want to be able to boot. using techniques in grub> root (hd0,0) setup (hd0) etc...

Is this technique necessary for a software RAID5 setup?

---

### Post by rsw686 on 2007-12-12
As long as the boot partition is not on the RAID 5 it is not necessary.

---

