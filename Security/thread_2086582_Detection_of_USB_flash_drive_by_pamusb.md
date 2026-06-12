---
title: "Detection of USB flash drive by pamusb"
date: 2012-11-21
forum: Security
---

### Post by PenguinNurse on 2012-11-21
Dear Ubuntu community,

The command ```
sudo pamusb-conf --add-device my_usb_pen
``` only detects my hard disk and not my mounted flash pen with vfat (also tried ext2, ext3 and ext4) file system, in order to use it for USB authentification.
What additional diagnostics could I run to pin down the problem?

Thanks in advance for your help!

---

### Post by PenguinNurse on 2012-11-22
By using ```
sudo pamusb -v --add-device="MyStick"
``` I was informed about a missing volume on the stick.
By using gparted, I was able to fix the problem.
However, after using ```
sudo pamusb-conf --add-user="me"
```,
```
pamusb-check me
``` tells me
```
* No device configured for "me".
```
The file /etc/pamusb.conf seems to be correct.

---

