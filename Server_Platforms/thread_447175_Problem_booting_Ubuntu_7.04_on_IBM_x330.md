---
title: "Problem booting Ubuntu 7.04 on IBM x330???"
date: 2007-05-17
forum: Server Platforms
---

### Post by atarimaster on 2007-05-17
I recently was given an IBM x330 server, and would like to install Ubuntu Server 7.04 on it. I used a pci vga card to hook the monitor up because I do not have the C2T breakout cable. The problem came when I booted it up and was not able to use the initial boot screen because the USB keyboard was not deteced. I figured this was because USB is not initialized on boot. There are no PS/2 ports on the server so that is not an option. 

question: 
How do I bypass the initial select startup sceen, so I  can install Ubuntu?

---

### Post by blazercist on 2007-05-22
this may be a stupid answer, usb keyboard support is not from the OS but from BIOS, you should check your BIOS settings , wait wait, you can't even ESC to BIOS, without a keyboard lol, try removing the CMOS battery and replacing it, that should restore factory defaults and then you should be all good.

---

