---
title: "nvidia driver 440 results in desktop failing to load - RTX 2070 Super"
date: 2020-04-09
forum: Ubuntu Development Version
---

### Post by Psychobudgie on 2020-04-09
Hi,

Installing the proprietary nvidia drivers (tested) results in the 20.04lts Beta failing to move beyond the login page. If I switch to a terminal (e.g. alt-shift F2) you can see the desktop appear as a ghosted image behind the text based terminal display suggesting the drivers have loaded.

Drivers work fine in 18.04lts with latest updates but have previously had similar issues in 19.10 which led to me sticking with the previous LTS release. Has anyone had similar issues or have a fix I can try to implement?

---

### Post by CelticWarrior on 2020-04-10
Please disable Secure Boot in UEFI.

---

### Post by Psychobudgie on 2020-04-12
It is disabled. Previous LTS release is working fine with the same driver.

---

### Post by CelticWarrior on 2020-04-12
```
sudo apt-get purge nvidia*
```

and then reinstall the drivers correctly. Meaning: Install from the official repositories.

---

### Post by Psychobudgie on 2020-04-12
Did that, didn't work. I'm currently reinstalling from scratch in case I've missed something.

---

### Post by Psychobudgie on 2020-04-12
Ok, double checked secure boot is off, flattened and did a complete reinstall, reinstalled nvidia-driver-440 from official repos and same result. See the attached screenshot to see what greets me on switching to a TTL

I am logged in and according to top, the desktop is running but other than the ghosted image buffer on the terminal display I can't get to it.

Completely stumped. [ATTACH=CONFIG]285499[/ATTACH]

Edit :

Ok, if I kill GDM via a terminal and then use startx, I get a fully working gnome session complete with fully functioning nvidia drivers which lead me to think this is an Ubuntu specific issue but no idea what.

---

### Post by Psychobudgie on 2020-04-12
I've found a couple of old posts on switching from GDM3 to Light DM as a fix for a similar issue with 19.04 so will try and report back

---

### Post by Psychobudgie on 2020-04-12
and voila. Installing and switching to LightDM fixes the issue which seems to be related to GDM3 which would correspond to why 18.04LTS didn't show the issue as it also used LightDM by default.

---

### Post by rbmorse on 2020-04-12
I have a RTX 2080 running on the 440.64 drivers in 20.04 using GDM.  No problems.

---

### Post by Psychobudgie on 2020-04-12
Problem didn't happen with my RTX 2060, just the 2070 super. Still can't find a specific reason for it unless it's something specific to the particular 2070 super (Palit GeForce RTX 2070 SUPER JS) that's causing the issue combined with the motherboard (ASUS ROG asus rog strix z390-f). 

Whatever it is, switching to LightDM deffo resolves the issue here.

---

### Post by WildSioux on 2020-04-15
I recently ran into this problem when I installed 20.04 with Nvidia.  If you have auto login enabled it won't get past login screen.  Edit grub and Delete the "splash" in GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1845801](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1845801)

---

### Post by Psychobudgie on 2020-04-17
You sir, are a star!

---

