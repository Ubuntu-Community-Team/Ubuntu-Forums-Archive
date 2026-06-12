---
title: "cryptsetup: Can not access device - after upgrading to jaunty"
date: 2009-05-13
forum: Security
---

### Post by mveltre on 2009-05-13
hi,

I recently upgraded a 8.10 to 9.04 by the upgrade manager. When trying to mount some hard-drives, I get an error:

/sbin/cryptsetup luksOpen /dev/sda3 sda3crypt
Aufruf fehlgeschlagen: Can not access device

This occurs on any of the cryptsetup devices, also by using keyfiles. The command worked for me until 8.10, the device is there (fdisk -l).

Any ideas? 

Thanks!
Markus

---

### Post by mveltre on 2009-05-13
CLOSED .... ;-)

sry, the new kernel just re-arranged my partition table and I did not noticed it when looked at fdisk -l.

Thanks anyway,
Markus

---

