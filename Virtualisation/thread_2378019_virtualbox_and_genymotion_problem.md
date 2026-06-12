---
title: "virtualbox and genymotion problem"
date: 2017-11-19
forum: Virtualisation
---

### Post by sasankashekhar2000 on 2017-11-19
i downloaded the latest version of virtualbox in my ubuntu 16.04lts.
i got genymotion too and successfully installed both of them. then i downloaded some virtual devices and tried to start them but they dont start and error comes and tells me to start via virtualbox
when i tried to open via virtual box this error came
 VT-x is disabled in the BIOS for all CPU modes
 (VERR_VMX_MSR_ALL_VMX_DISABLED).

please tell me what do i do???
i'm a newbie and dont know much bout ubuntu

---

### Post by vasa1 on 2017-11-19
Moved to the appropriate sub-forum.

---

### Post by ajgreeny on 2017-11-19
Fot that VT-x problem you need to go into your BIOS or UEFI setup; you will probably see a message flash on screen at power-on with the key to press to enter setup, but often it's Del or F2.  If you don't see a message look in the motherboard info you should have, or be able to search for on the web.

When in the setup look for a setting for Virtualisation in one of the pages.
See [https://askubuntu.com/questions/256792/how-do-i-enable-hardware-virtualization-technology-vt-x-for-use-in-virtualbox](https://askubuntu.com/questions/256792/how-do-i-enable-hardware-virtualization-technology-vt-x-for-use-in-virtualbox) for all details.

---

