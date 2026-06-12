---
title: "USB problems - ehci_hcd module"
date: 2008-03-18
forum: Server Platforms
---

### Post by SumnerBoy on 2008-03-18
Hi, 

I have been trying to get my Canon MP530 multi-function device to scan using saned but have been getting "Error during device I/O" errors. I have been searching various forums to try and work out what is wrong and came across a few posts that mention the ehci_hcd module causes problems with some USB devices. 

I ran 'sudo modprobe -r ehci_hcd' which unloads the module and now my scanner works. However now my external USB drive is no longer recognised. If I then run 'sudo mount -a' the external USB drive is remounted ok, and the scanner remains functional. So all is good - however upon rebooting I am back to square one...

I understand the ehci_hcd module is related to (or is) the USB2.0 module - is this correct? Why is it causing problems with my Canon MP530? The printer function was working fine, it is just the scanner causing problems.

I tried adding the 'modprobe -r ehci_hcd' command to my /etc/rc.local script, before the 'mount -a' command I had previously added to ensure my USB drive was mounted correctly on boot, but this resulted in the scanner working ok, but the USB drive failing to mount.

I also tried adding ehci_hcd to /etc/modprobe.d/blacklist but this didn't appear to make any difference.

Can anyone help me here? It seems I can get things working by manually running the modprobe -r ehci_hcd command and then remounting the USB drive, but I want this to be automatic on a reboot.

Thanks in advance!

---

