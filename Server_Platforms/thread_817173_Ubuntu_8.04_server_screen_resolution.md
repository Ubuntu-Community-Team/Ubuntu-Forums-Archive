---
title: "Ubuntu 8.04 server screen resolution"
date: 2008-06-03
forum: Server Platforms
---

### Post by spewperb on 2008-06-03
Hi, I have just installed ubuntu server 8.04 onto a sony vaio laptop. All is working fine however the screen resolution isn't full screen. Is it possible to adjust the resolution in a server, terminal view only environment?

---

### Post by cdenley on 2008-06-03
If I remember correctly, you can change the terminal's resolution using a boot option like "vga=791" in /boot/grub/menu.lst, replacing 791 with the correct mode. Many laptops force the lcd to display at it's native resolution. I think terminals use 640x480 by default, so if the lcd was displaying 1024x768, it would display your 640x480 screen in the middle of a black border. You might have a bios setting to change this.

This might help
[https://wiki.ubuntu.com/FrameBuffer#head-e4c604e0cdd1495d244e7bd07dfdc413a5aaf4e8](https://wiki.ubuntu.com/FrameBuffer#head-e4c604e0cdd1495d244e7bd07dfdc413a5aaf4e8)

---

