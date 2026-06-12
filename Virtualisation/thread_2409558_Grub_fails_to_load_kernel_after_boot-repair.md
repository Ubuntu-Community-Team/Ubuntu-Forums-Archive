---
title: "Grub fails to load kernel after boot-repair"
date: 2019-01-03
forum: Virtualisation
---

### Post by jo2019 on 2019-01-03
I have an **Ubuntu 14.04** running in a **VirtualBox VM** with **Windows 10** Host. My problem started while installing the requirements for a package HIDAPI which required other packages such as Hidraw. I noticed the installation process was messing with GRUB and some point went to a black screen. After powering on the VM again, the boot menu was just memtest.

I tried to recover the Grub in several ways:
Manually ([https://www.vijaytechnology.com/2011/06/grub-rescue-from-live-ubuntu-cd/](https://www.vijaytechnology.com/2011/06/grub-rescue-from-live-ubuntu-cd/))
Boot-repair ([https://ubuntuforums.org/showthread.php?p=10871917#post10871917](https://ubuntuforums.org/showthread.php?p=10871917#post10871917))

I run Boot-repair 3 times because the first one failed at purge of grub-install. 
The second one, resulted into no boot menu and booting directly into grub console. Within Grub console I couldn't load the file **initrd.img** although it was there.
The third time, I got boot menu with the following options.
[ATTACH=CONFIG]282092[/ATTACH]

However, by either choosing Ubuntu or Advance->recovery mode, the booting process gets stuck as follows:

[ATTACH=CONFIG]282093[/ATTACH]

This is the report of Boot-Repair
[http://paste.ubuntu.com/p/t2YxW5ySPD/](http://paste.ubuntu.com/p/t2YxW5ySPD/)

I would appreciate any help to recover my VM.

---

### Post by wildmanne39 on 2019-01-03
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

