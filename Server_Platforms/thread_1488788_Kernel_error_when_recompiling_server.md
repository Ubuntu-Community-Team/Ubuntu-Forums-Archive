---
title: "Kernel error when recompiling server"
date: 2010-05-20
forum: Server Platforms
---

### Post by Daleth on 2010-05-20
Greetings, I seem to have a problem when I try to recompile my kernel to other settings, tried to follow several guides on forums and guides found on google, but it keep getting the same error when the compile has finished and the computer is rebooted, the error is something like this:" Kernel Panic - unable to mount root fs on unknown"

Trying to recompile on the newest ubuntu server release 64 bit on a dual core computer. Could be grub thats messing with the settings or is it something when I install ubuntu from scratch *using guided format* 

Thank you.

---

### Post by Bachstelze on 2010-05-20
Chances are that support for either your ATA chipset or your root filesystem (or both) is missing from your kernel.

---

