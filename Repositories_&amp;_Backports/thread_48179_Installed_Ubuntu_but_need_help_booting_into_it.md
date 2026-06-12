---
title: "Installed Ubuntu but need help booting into it"
date: 2005-07-11
forum: Repositories &amp; Backports
---

### Post by viciouspoultry on 2005-07-11
I want to create a dual boot system with Windows and Ubuntu and I already installed Ubuntu on one of my partition I created before hand, it is a ext2 filesystem, during the installation I tried loading the GRUB but it didn't work. After the installation I got booted into Windows XP, but I want the option to boot into Ubuntu. I checked in partition magic and the Ubuntu partition has exactly 350.4 mb in it, so I'm guessing it installed right. So now how do I boot into Ubuntu while having the option to go into Windows?

Do I have to create another GRUB file or edit boot.ini? Or did I mess up my installation and need to reinstall it?

---

### Post by Skrewdriver on 2005-07-12
Does it boot into GRUB or go straight to windows?

---

### Post by UbuWu on 2005-07-12
Maybe you installed grub to the ubuntu partition while it should be installed in the first partition, which is probably the one windows is on. This can probably be fixed using the live cd, although I can't tell you exactly how.

---

