---
title: "Grub"
date: 2006-02-13
forum: The Cafe
---

### Post by jrincon87 on 2006-02-13
Hey. I use Ubuntu but installed Mepis in another partition just to try it out. I have some time without using Linux and I though that inside the installation of Mepis, it was gonna ask me which OS I wanted to select in the GRUB. But in fact, it didn't. Now I can only enter to Mepis and Windows and not to Ubuntu. Is there a way that I can switch back to the Ubuntu Grub? (it's easier for me because I don't remember my kernel version and all that stuff since I have done many upgradings to Ubuntu). I think that could be done with Lilo by making something like lilo -u *something else*.
Thanks.

---

### Post by Gandalf on 2006-02-13
-> [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)

---

### Post by ajgreeny on 2006-02-13
Get hold of a copy of explore2fs for windows and you will be able to read your menu.lst file in grub/boot when booted into windows.  You should then be able to add the appropriate entry to your grub menu in mepis.

This is also a good reason for copying your grub menu.lst to floppy if you have one, because you can always copy a changed grub list back to your mbr.

---

