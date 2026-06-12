---
title: "Ubuntu 13.04 Updated - won't boot"
date: 2013-08-21
forum: Ubuntu, Linux and OS Chat
---

### Post by naviathan on 2013-08-21
Ok the title is a bit misleading, it will boot, once I edit the grub menu and tell it to load /dev/sda1 as the root device. Otherwise it attempts to load /dev/sda (no partition number) as root which obviously fails. I tried running a grub-mkconfig once I got back in to hopefully update the thing, but it still insists that /dev/sda is the root device. Something in the grub.d scripts has changed, has anyone else had this issue? I knew I shouldn't have rebooted...

---

### Post by naviathan on 2013-08-21
Fixed it! Looks like the update deleted the device.map and didn't regenerate one. Anyway, I generated a device.map and ran grub-mkconfig again and it updated properly.

---

