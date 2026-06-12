---
title: "eSATA port multiplier problems with 12.04 LTS server install"
date: 2012-04-28
forum: Server Platforms
---

### Post by MakOwner on 2012-04-28
Anyone else seeing issues with port multipliers and 12.04 server install?
From the same hardware running 10.04 and booting from a cold start with no issue, 12.04 will consistently drop to the initiramfs prompt after a really ugly time trying to initiate and spin up disks in an external enclosure.

I see the "Do you want to start the raid array in a degraded state [Y/N]" about the last iterations of the port resets and the drive lights come on steady.  

And there are some really ugly attempts to kill udev processes during boot.

As soon as the boot process halts at the initramfs prompt, I can hit control+d and the boot process resumes and the array comes up clean and the filesystem mounts.

-------------------
RAID BIOS needs to be enabled on the card, even if you are just using software raid with JBOD.

---

