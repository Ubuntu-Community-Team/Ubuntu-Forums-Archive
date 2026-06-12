---
title: "Installation woes for Ubuntu Studio 14.04: no mouse, no net"
date: 2014-06-09
forum: Ubuntu Studio
---

### Post by Petra Roosen on 2014-06-09
Hello,

i had severe troubles in installing the freshly downloaded 32 bit 14.04 version: Starting with a USB stick worked flawlessly, but trying the first reboot after filling the harddisk with the base system made the computer (Lenovo ThinkPad T60p) dysfunct. **No net connection, no mouse interaction; keyboard works.**

I finally found the problem myself: The USB stick works consistently with a kernel version 3.13.0-29-lowlatency and everything is okay. After installation the computer is equipped with the same kernel, but with a module set at /lib/modules prepared for 3.13.0-24-lowlatency. **The directory branch /lib/modules/3.13.0-29-lowlatency from the stick was NOT copied to the harddisk during the installation procedure.** Hence: No functionality that is provided by the modules. Copying the respective directory sub-tree from stick to disk resolved the issue. Now everything seems to work fine (so far as I have tested it).

This message intends to help other people that get stuck with the same problem.

Cheers,

Petra

---

