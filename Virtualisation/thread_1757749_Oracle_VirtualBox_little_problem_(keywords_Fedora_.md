---
title: "Oracle VirtualBox little problem (keywords: Fedora 14, ISO image, 64-bit)"
date: 2011-05-13
forum: Virtualisation
---

### Post by 3602 on 2011-05-13
So I'm giddy that I don't have to burn these images to actual CDs to install them in VB.
Thing is, VirtualBox will start it, I see the blue Fedora screen with the ten-second auto-boot countdown timer, then... nothing. The Fedora screen is right there, but with nothing else. No words, no dialog box, nothing.
I thought about a permission thing and *sudo mv* this ISO image down to /. Same thing.
The image is 64-bit.

How to get it working?

Thank you very much. This shall allow me to toy with other distros before actually multi-booting them.

---

### Post by 3602 on 2011-05-13
Solved by enabling BIOS hardware virtualization (HP SVM).

---

