---
title: "Grub 2 problem on 10.4"
date: 2010-05-17
forum: Server Platforms
---

### Post by K_V_B on 2010-05-17
Hello,

I want to play around with XEN, and for this I need to add my own entry to the grub config.
According to the (very limited) information I have I need to add a "menuentry" to 40_custom in /etc/grub.d. 
So I did.
40_custom now contains:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Xen 4 Ubuntu 2.6.31.6-xen1'{ 
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    multiboot (md0)/xen-4.0.0.gz dummy=dummy dom0_mem=1024M
    module (md0)/vmlinuz-2.6.31.13xen-kvb-1 dummy=dummy root=/dev/mapper/thunersee_root-root ro 
    module (md0)/initrd.img-2.6.31.13xen-kvb-1
} 

After running upgrade-grub I notice that the entry has been added to /boot/grub/grub.cfg, but when I reboot the entry isn't there in the boot menu.

So it appears that there is something about the entry that grub doesn't like. But what? The grub website doesn't even have any documentation about what the correct syntax for menuentry is. 
Can anybody help me? What do I need to add to my grub config to boot XEN?

---

### Post by K_V_B on 2010-05-21
* Bump *

Is there really nobody here that can me give some hints that would help me further?

Basically I would really like to know why my menuentry isn't turning up in the grub menu. Why is it completely ignored by grub?
It is in grub.cfg, together with the entries that were created automatically, and which are shown.

---

### Post by alfredocambera on 2010-09-16
Just execute update-grub

---

