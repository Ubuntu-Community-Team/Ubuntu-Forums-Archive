---
title: "Disable core(s) of a CPU 11.04"
date: 2011-09-08
forum: Server Platforms
---

### Post by dimothy10 on 2011-09-08
I am setting up an ubuntu box to do some OCR for us and have some software ready to go.  The license however limits me to a single core.  Quick google search shows that editting grub.conf and adding maxcpus=1 will do the trick.  However I seem to remember there being some changes to GRUB and as such I cannot find grub.conf anywhere.  Is there another way to disable a single core of my dual core CPU or is there a way to ammend GRUB without a grub.conf file?

Reagrds

Tim

---

### Post by Entilza on 2011-09-08
check /etc/default/grub

Then use:

sudo update-grub

It will modify /boot/grub/grub.cfg  (Don't change this manually or it will be overwritten the next time you do update-grub.

---

