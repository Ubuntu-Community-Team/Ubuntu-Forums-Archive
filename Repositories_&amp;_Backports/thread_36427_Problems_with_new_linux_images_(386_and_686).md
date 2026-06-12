---
title: "Problems with new linux images (386 and 686)"
date: 2005-05-23
forum: Repositories &amp; Backports
---

### Post by jkndrkn on 2005-05-23
It seems that a new version of the 386 and 686 linux images are available. I used synaptic to attempt to install them and ran into a problem. The 386 image seemed to install correctly. However, the 686 image failed to install. An error message was generated indicating that files relating to the ndiswrapper could not be installed.

I booted into the 386 kernel to find that ndiswrapper was failing to load properly and that my nvidia drivers were not working; I was forced into command line.

Can I assume that the nvidia drivers and ndiswrapper files will need to be reinstalled after the updating of the linux image files?

What other considerations should I make while upgrading the linux kernel image?

Thank you.

---

### Post by netrattler on 2005-05-23
For your 686 kernel it sounds like for some reason it didn't install the linux-restricted-modules. so all you need to do from your terminal is type

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-restricted-modules-686

and then everything should be working for your 686 kernel again.

Joe

---

### Post by pdk001 on 2005-05-23
since i did to updating 686 kernel, i can't automatically booting with windows XP(i have to hit the"windows XP" in grub list to boot)

---

### Post by jobezone on 2005-05-23
[QUOTE=pdk001]since i did to updating 686 kernel, i can't automatically booting with windows XP(i have to hit the"windows XP" in grub list to boot)[/QUOTE]

You can edit the file /boot/grub/menu.lst
and change the default entry to boot. Right at the top, there should be
default                <some number>

you must change that number, so, if for example winxp is the 4th entry in the grub list, it should be:

default                4

If this entry has a # before it, delete the # or else this option is not used.

---

