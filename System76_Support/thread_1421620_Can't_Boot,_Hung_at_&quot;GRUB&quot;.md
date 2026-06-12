---
title: "Can't Boot, Hung at &quot;GRUB&quot;"
date: 2010-03-04
forum: System76 Support
---

### Post by Futurian on 2010-03-04
My Panp5 has been running Karmic just fine for some time. I recently created a separate partition for Jaunty, so that I could use Nvidia's CUDA development tools (which don't yet work with Karmic). All went well until this morning, when the Update Manager wanted to update the linux kernel. I let it do that, but lost access to my Jaunty partition from the GRUB boot menu. I tried update-grub, among many other things, but still could not see the Jaunty partition from GRUB.

Hoping that GRUB2 would do better, I installed it, but still no access to the Jaunty partition. GPARTED showed the Jaunty partition (/dev/sda7) still there. I also had trouble with GRUB2, so I uninstalled it and reinstalled legacy GRUB.

I still couldn't see the Jaunty installation at on /dev/sda7 in the GRUB menu. 

At some point, I must have damaged something. Now my Panp5 just displays "GRUB" when I boot it, but won't go further.

I used a LiveCD and GParted to look at the disk. /dev/sda7 was listed as bootable, but /dev/sda1 was not. So I used GParted to make /dev/sda1 bootable. But booting still hangs at "GRUB"

Help! (and Thanks!)

---

### Post by psusi on 2010-03-04
The bootable flag is meaningless to anything but the DOS MBR.  Sounds like you need to reinstall grub to get it working again, then if you want the other OS on the menu, add it.

---

### Post by ubunterooster on 2010-03-04
use SystemRescueCD or Ubuntu's Live CD [select repair system in the CD's boot menu] to reinstall grub

---

### Post by Futurian on 2010-03-04
Thanks, good people! I reinstalled GRUB, and can now boot into my Karmic partition.

How would I add the Jaunty partition to GRUB? sudo update-grub didn't do it.

Thanks again, to both  psusi and ubunturooster.

---

### Post by psusi on 2010-03-04
Edit /boot/grub/menu.lst

---

### Post by Futurian on 2010-03-13
Thanks, you are a prince (or princess, as the case may be).

---

