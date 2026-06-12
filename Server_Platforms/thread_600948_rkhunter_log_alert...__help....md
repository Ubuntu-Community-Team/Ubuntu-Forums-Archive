---
title: "rkhunter log alert...  help..."
date: 2007-11-02
forum: Server Platforms
---

### Post by someoneouthere on 2007-11-02
i installed and ran rkhunter and eveythink seemed to be ok except this part of the log..:"....
[00:05:23] Checking for hidden files and directories [ Warning ]
[00:05:23] Warning: Hidden directory found: /etc/.java
[00:05:23] Warning: Hidden directory found: /dev/.static
[00:05:23] Warning: Hidden directory found: /dev/.udev
[00:05:23] Warning: Hidden directory found: /dev/.initramfs
[00:05:58] ......"

what does it mean?
__________________

---

### Post by k_grdn on 2007-11-02
They are just hidden files/dirs used by system and are harmless.

Edit /etc/rkhunter.conf

uncomment or add:

ALLOWHIDDENDIR=/dev/.udev
ALLOWHIDDENDIR=/dev/.static
ALLOWHIDDENDIR=/dev/.initramfs
ALLOWHIDDENDIR=/etc/.java


Regards,

k_grdn

---

