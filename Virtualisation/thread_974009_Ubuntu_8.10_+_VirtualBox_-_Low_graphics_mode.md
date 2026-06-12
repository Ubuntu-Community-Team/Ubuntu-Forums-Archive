---
title: "Ubuntu 8.10 + VirtualBox - Low graphics mode"
date: 2008-11-07
forum: Virtualisation
---

### Post by ubuntuubuntu on 2008-11-07
Hi, I use Ubuntu under VirtualBox. I've juts upgraded Ubuntu 8.04 to 8.10. Now, in startup, I get the message "Ubuntu is running in low-graphics mode

Your screen, graphics card, and input device settings
could not be detected correctly. You will need to
configure these yourself."

I've been told to try sudo dpkg-reconfigure xserver-xorg and sudo dpkg-reconfigure -phigh xserver-xorg, but neither worked.

What should I do?

Thank you!

---

### Post by ph4t3 on 2008-11-08
Hi, i apoligise in advance for any bad spelling. Im using a mobile phone, as im travelling at the moment.
I experienced a similar problem and eventually came to the conclusion that the error waz in my menu.lst . If u chose to keep the previously installed menu.lst, then your nvidia drivers might not be recognized when booting. A solution was to edit /boot/grub/menu.lst and change the kernal number there. I can't exactly remember the exact specifications, but i'll edit this post as soon as i get near a computer. Good luck...

---

### Post by portnoy1982 on 2008-12-03
You have to re-install VirtualBoxAdditions. After that it should be work.

---

### Post by osiris2258 on 2008-12-09
I am unable to reinstall guest additions. It tells me I have an "unsupported x86 environment" and stops.

---

