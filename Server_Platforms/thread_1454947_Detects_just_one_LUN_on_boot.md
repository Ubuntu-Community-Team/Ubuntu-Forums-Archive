---
title: "Detects just one LUN on boot"
date: 2010-04-15
forum: Server Platforms
---

### Post by BizonGod on 2010-04-15
Hello!
 I have RAID with few LUNs, but on boot Ubuntu detects just
first one. After using rescan-scsi-bus.sh it see all LUNs.
 Next problem is after using rescan-scsi-bus.sh I have
/dev/sg1 to sg3 , but only for sg3 /dev/sda is created, no map
for sg1 and sg2.

What shall I do to detect all LUNs on boot and map them correctly?

UPDATE:
Now mapping works fine. But still I have problem with
scan on driver bring-up. It scans just for LUN 0, and
nothing helps here: scsi_mod - max_luns, kernel params etc.
What to do to enable scanning for LUN > 0 at boot?

Thanks
Karol

---

