---
title: "Vista 64bit Install using Virtual Box on Ubuntu"
date: 2009-04-07
forum: Virtualisation
---

### Post by mattldn on 2009-04-07
I have an AMD64 bit processor, and running the 64bit Ubuntu perfectly; I am having trouble installing the 64 bit version of Vista Ultimate using VirtualBox. I receive the following errors when I attempt to install:

File: \windows\system32\boot\winload.exe
Status: 0xc000055A
Info: Attempting to load a 64-bit application, however this CPU is not compatible with a 64-bit mode.

If anyone has successfully installed VISTA 64 using Virtual Box on a Ubuntu 64 bit, I would appreciate any help given.

---

### Post by Perryg on 2009-04-07
> **mattldn said:**
> I have an AMD64 bit processor, and running the 64bit Ubuntu perfectly; I am having trouble installing the 64 bit version of Vista Ultimate using VirtualBox. I receive the following errors when I attempt to install:

File: \windows\system32\boot\winload.exe
Status: 0xc000055A
Info: Attempting to load a 64-bit application, however this CPU is not compatible with a 64-bit mode.

If anyone has successfully installed VISTA 64 using Virtual Box on a Ubuntu 64 bit, I would appreciate any help given.

Which VBox are you using?  Is it 64 bit?
In the VBox setup did you turn on VT-X/AMD-v  and Nested Paging?

---

### Post by hotrod02 on 2009-08-28
I am experiencing the same issue.  I am using Ubuntu (Jaunty) and Sun Virtual Box.

---

### Post by Perryg on 2009-08-28
> **hotrod02 said:**
> I am experiencing the same issue.  I am using Ubuntu (Jaunty) and Sun Virtual Box.

64 bit OSes in VirtualBox require that you have hardware-v turned on in your PC bios.  Look at your bios and make sure that it is turned on.  If you can not find it then your PC does not support hardware-v and you will not be able to install a 64 bit OS in VirtualBox.

---

