---
title: "Grub2 ( /boot ) on compact flash ( CF ) card doesn't show new kernels"
date: 2012-01-22
forum: Server Platforms
---

### Post by janmyszkier on 2012-01-22
Last time i put up a system i decided to put boot partition onto separate drive(because of raid). So i connected CF to IDE connector and used old CF card. 

but recently I realized it doesn't update the listing. Don't blame me, I don't reboot it too often ;) however, since 3.0.0-12 i don't get any list updates. 

Can the fact that is it on separate disk change anything? update-grub says it finds 3.0.0-15 but i don't see it on the listing when i see grub onscreen.

Please advice on possible fixes

---

### Post by janmyszkier on 2012-01-26
fixed the error. my cf card was the boot device (bios setting)
but after the system booted-up, the boot on raid partition took the /boot location.

what I did was edit /etc/fstab and re-assign my CF card to /boot.

this fixed it, and topic can be closed/deleted.

---

