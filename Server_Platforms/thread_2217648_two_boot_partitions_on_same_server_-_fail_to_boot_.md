---
title: "two /boot partitions on same server - fail to boot due to raid degraded mode"
date: 2014-04-18
forum: Server Platforms
---

### Post by rollyah on 2014-04-18
trying to get mdadm --detail of the array puts the whole system into an unresponsive mode which is why i had to reboot.
the system was running on raid10 , even though it's set to boot even in degraded mode, it didn't.

the collocated DC support installed a whole new ubuntu server OS on a new disk that they plugged in.
when they rebooted my server it goes to the old config and fails to boot, instead of going through the new installed system.

Info:
- Bios settings is set to boot the new disk (which in concept, should load the newly set /boot partition and proceed)
- changing fstab on the new system wouldn't make a difference (or it would ?) because it's not even being read (or is it?) as the system is reading the old grub config
- the "/" partition of the old system isn't accessible, so i'm not sure why is the system deciding to boot to it

Any help on how to troubleshoot this issue would be greatly appreciated

Note: could it be that my newly installed grub has the old system as its top selection to boot from? i'm not sure how to check as it just shows the UUID of the device and im not sure which is old and which is new..

---

