---
title: "udevadm not reporting &quot;serial&quot; number"
date: 2011-11-04
forum: Server Platforms
---

### Post by Markus_ch on 2011-11-04
Hi,
I recently installed Ubuntu 11.04 x64 fileserver with 3 disks in ZFS pool (3x Seagate 2TB ST2000DL003-9VT166).
I did try to prevent problem with out of order mounting the drives by specifying udev rule, however I can not determine unique identifier of the disks.
"udevadm" is not reporting the "ATTRS{serial}" attribute. hdparm command does find the serial and also all other parameters just fine.
Do you have any ideas how to work around the issue?

Attached are the 'udevadm info -a -p $(udevadm info -q path -n /dev/sdX)' listings, aswell as hdparm output for sdb (for comparsion)

Thank you!

---

### Post by Markus_ch on 2011-12-22
Issue solved. Solution found here:
[http://www.linuxquestions.org/questions/linux-hardware-18/udev-rules-fail-on-identical-sata-hard-disk-drives-584595/](http://www.linuxquestions.org/questions/linux-hardware-18/udev-rules-fail-on-identical-sata-hard-disk-drives-584595/)

In short, I used "ENV{ID_SERIAL_SHORT}" in the udev rule which helped.

---

