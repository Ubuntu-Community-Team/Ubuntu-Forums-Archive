---
title: "Raid fail message after upgrade"
date: 2012-02-15
forum: Server Platforms
---

### Post by sarte on 2012-02-15
So I upgraded my server (Ubuntu 10.04.4 LTS) and got following error:

Setting up grub-pc (1.98-1ubuntu13) ...
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-server
Found initrd image: /boot/initrd.img-2.6.32-24-server
Found memtest86+ image: /boot/memtest86+.bin
ERROR: pdc: wrong # of devices in RAID set "pdc_dgcdbgbiii" [1/2] on /dev/sda
ERROR: pdc: wrong # of devices in RAID set "pdc_dgcdbgbiii" [1/2] on /dev/sda
done

That doesn't look like an error I'd like to see. Fortunately there is no need reboot anytime soon, but what should I expect when making my next restart? Also any ideas how to fix this problem would be greatly valued.

My RAID controller is  ATI Technologies Inc SB700/SB800 SATA Controller

---

### Post by sarte on 2012-02-16
Could someone even explain what the error actually means? Google doesn't seem to give that many hits on this issue.

---

