---
title: "Win XP  Virtualization Problem"
date: 2011-07-31
forum: Virtualisation
---

### Post by EarlyLinuxLover on 2011-07-31
[SIZE=2]Hello All,

I am currently running  [/SIZE][SIZE=2]Ubuntu 11.04 (Natty Narwhal), and have attempted to install Win Xp SP2 using using the latest version of virtualbox and Aqemu (a KVM frontend), but during the install process the setup program complains about not be able to copy certain files, and gives a choice between ignoring the error or continuing, so i go ahead and have it continue, and XP installs but certain things like Media Player doesn't work, and when I try to install any windows software, it doesn't seem to be able to recognize the install executable.

Can anyone help??! [/SIZE][B][SIZE=1]
[/SIZE][/B]

---

### Post by 73ckn797 on 2011-07-31
[SIZE=2]I have not used [/SIZE][SIZE=2]Aqemu but installing WinXP in Virtualbox was no different than installing WinXP normally. Maybe try installing without [/SIZE][SIZE=2]Aqemu. I have never seen the need to use anything but Virtualbox reading the Windows CD.
[/SIZE]

---

### Post by Jake.Debord on 2011-08-04
Could be a corrupt image.

---

### Post by x-D on 2011-08-06
> **Jake.Debord said:**
> Could be a corrupt image.

More likely to be a corrupt Image as stated in the above post. I would recommend installing without that Front-End you used, another thing is, try and Dual boot it with Ubuntu, install it regularly from the CD. Then using the Live Disk of Ubuntu use Boot-Repair (search my threads and posts or the internet) on how to get Boot-Repair to reinstall GRUB as the bootloader and then do:

```

sudo update-grub

```

(It may work without this, but just to be 100% sure :) -)

---

