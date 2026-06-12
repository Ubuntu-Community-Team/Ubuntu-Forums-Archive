---
title: "kernel quandries?"
date: 2005-06-13
forum: The Cafe
---

### Post by somuchfortheafter on 2005-06-13
I noticed that nomatter where I install ubuntu I get the default i386 kernel which is all fine and dandy but nobody needs i386 is there any way that ubuntu could get a smart installer to remove the kernel and install the correct kerenl ie k7/i686?

---

### Post by Xian on 2005-06-13
I've not tried it but since the installer is Debian based will it let you do an expert install by passing that parameter at the boot line?

$ linux expert

---

### Post by poofyhairguy on 2005-06-13
[QUOTE=somuchfortheafter]I noticed that nomatter where I install ubuntu I get the default i386 kernel which is all fine and dandy but nobody needs i386 is there any way that ubuntu could get a smart installer to remove the kernel and install the correct kerenl ie k7/i686?[/QUOTE]


Its easy to install and use the 686 kernel. 

sudo apt-get install linux-686

then reboot.

---

