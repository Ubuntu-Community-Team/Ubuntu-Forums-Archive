---
title: "Jaunty framebuffer issues"
date: 2009-05-26
forum: System76 Support
---

### Post by retrovertigo on 2009-05-26
On my Serval Pro, once X starts up I have no virtual terminals when I press Ctrl-Alt-F1 through F6.  I have made the following changes to the default Jaunty install:

1) Enabled restricted nVidia driver
2) Installed System76 driver
3) Added **vesafb**, **nvidiafb**, and **fbcon** to /etc/initramfs-tools/modules
4) De-blacklisted **vesafb** and **nvidiafb** in /etc/modprobe.d/blacklist-framebuffer
5) Ran **sudo update-initramfs -u -k all**
6) Appended **vga=0x369** (for 1680x1050x24 resolution) to the kernel entry in /boot/grub/menu.lst and ran **sudo update-grub**
7) Updated resolution to 1680x1050 in /etc/usplash.conf and ran **sudo dpkg-reconfigure usplash**

Once I reboot my computer, the bootsplash looks fine, and I can hit Alt-F1 and see the detailed information as services start, but once X starts I get nothing when I try to switch to a virtual terminal.  My Serval has an nVidia GeForce GTX 260M video card.

Any thoughts?

---

### Post by thomasaaron on 2009-05-27
This is a known nVidia bug. Please see...
[http://ubuntuforums.org/showthread.php?t=1075783&highlight=virtual+terminal](http://ubuntuforums.org/showthread.php?t=1075783&highlight=virtual+terminal)

---

