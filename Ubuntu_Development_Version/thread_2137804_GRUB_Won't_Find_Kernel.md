---
title: "GRUB Won't Find Kernel"
date: 2013-04-22
forum: Ubuntu Development Version
---

### Post by fowlslegs on 2013-04-22
I just upgraded from Xubuntu 12.10 to Ubuntu 13.04 using `sudo do-release-upgrade -d`. I accidentally turned my computer off during the upgrade process when I meant to restart xscreensaver and some other x program which the terminal-based installation prompt said I needed to halt. Anyway it seemed I had resolved everything after remounting my sda1(root) partition and entering `dpkg --configure -a` from kernel 3.8.8's recovery mode, which I selected from the grub2 menu during bootup. I installed all raring updates and fixed my /etc/apt/sources.list. Everything seemed to be working fine. `uname -r` returned 3.8.8.x...-generic, `sudo update-grub`, however only found memtest. I made a mental note of this and meant to reinstall the kernel and figure out why grub wasn't seeing it even though it was obviously in use. However, I forgot and rebooted after updating. I am now immediately taken to memtest. (Oh yeah I set the grub timer to 0 and holding shift does nothing). What can I do? Kernel 3.8.8.x...-generic is definitely on my computer somewhere.

---

### Post by dino99 on 2013-04-22
into a terminal (ctrl+alt+t), run:
sudo apt-get purge grub-pc grub-common
sudo grub-install /dev/sda
sudo update-grub

---

### Post by fowlslegs on 2013-04-22
> into a terminal (ctrl+alt+t), run:
sudo apt-get purge grub-pc grub-common
sudo grub-install /dev/sda
sudo update-grub

Seems reasonable if it were not true:

> I am now immediately taken to memtest.

---

### Post by JMB74 on 2013-04-22
Might help? [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by fowlslegs on 2013-04-22
Yeah thanks JMB74. I actually thought of this before reading your reply and already fixed it. Came here on my working pc to close this thread up.

---

### Post by fowlslegs on 2013-04-22
...Except I'm not sure how.

---

### Post by dino99 on 2013-04-22
> **fowlslegs said:**
> ...Except I'm not sure how.

on your first post, click on "edit" then "advanced" on bottom right corner, then set "closed" as usual.

---

