---
title: "Testing raid, boot degraded doesn't work"
date: 2011-03-04
forum: Server Platforms
---

### Post by kylegio on 2011-03-04
Setup the software raid to boot degraded, first tried editing /etc/initramfs-tools/conf.d/mdadm setting "BOOT_DEGRADED=false" to "BOOT_DEGRADED=true"

didn't seem to have any effect, system did not attempt to boot degraded at all.

so i tried "dpkg-reconfigure mdadm" and went through the set up and configured it to boot degraded. 

the changes took affect this time, but the system still can not boot in a degraded mode. 

when trying to boot i get this output
```
Attempting to start the RAID in degraded mode...
mdadm: CREATE user root not found
mdadm: CREATE group disk not found
mdadm: SET_ARRAY_INFO failed for /dev/md0: Device or resource busy
mdadm: /dev/md1 has been started with 5 drives out of 6
could not start the RAID in degraded mode.
Gave up waiting for root device. Common problems:
***etc***
ALERT! /dev/disk/by0uuid/***UUID HERE*** does not exist. Dropping to shell!

BusyBox v1.153 ***etc***

(initramfs)_
```

---

### Post by ian dobson on 2011-03-05
Hi,

did you update your inital ram disk after changing the BOOT_DEGRADED option? This is necessary as when the system boots it loads the initram disk (that contains the config option) and then tried assembling/mounting the root array.

Regards
Ian Dobson

---

