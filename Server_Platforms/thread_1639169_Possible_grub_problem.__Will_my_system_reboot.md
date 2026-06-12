---
title: "Possible grub problem.  Will my system reboot?"
date: 2010-12-06
forum: Server Platforms
---

### Post by Devo66 on 2010-12-06
I have a 10.04 64 bit machine running as a vm server.  It's running software RAID 1.  I just did some updates and although it didn't install anything that requires a reboot (no kernel update) it felt the need to reinstall grub.  During the reinstall it spat out several of the following errors:

grub error: Out of partition.

and then said that installation finished and no errors were detected.  Afterwards I tried a manual update as well by running:

grub-install /dev/sda

and I got the same message.  Also happens with /dev/sdb.  Those are my two physical drives.  Root is mounted at /dev/md0 which comprises /dev/sda1 and /dev/sdb1.  Googling, I've see references to this out of partition error at boot, but not during a grub update.  

So, my question is this.  Will my system reboot?  I haven't attempted a reboot yet, since this happened.

---

### Post by arrrghhh on 2010-12-06
I didn't think it was advised to have the root partition on a RAID array, unless it's hardware RAID.

In theory you would want to install GRUB to md0, but I'm not sure in this case...

---

### Post by Devo66 on 2010-12-10
Well, finally got a chance to go on-site and reboot the server.  It booted up just fine.  I guess this was an erroneous error.

---

