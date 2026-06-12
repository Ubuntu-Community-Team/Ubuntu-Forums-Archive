---
title: "Elementary OS won't boot after installation."
date: 2014-08-21
forum: Ubuntu/Debian BASED
---

### Post by jon60 on 2014-08-21
I have Windows 7 and installed E OS like such:
[IMG]http://i.imgur.com/bvxSWrj.png?2[/IMG]

After the installation, I restarted the computer and took out the USB, but it went straight to Windows. I've had successful installations and boots with Ubuntu and MInt, but for some reason this isn't work. When I try the boot repair, it says is cancelled the purge. Also, I've tried EasyBCD to no success. What can I do?

This is the boot info summary: [http://paste2.org/DgCNsV2I](http://paste2.org/DgCNsV2I).

---

### Post by jon60 on 2014-08-23
Thanks for all of your help, I've now fixed it by removing it.

---

### Post by Stinger on 2014-08-25
Hi jon60
If you are using Luna and the advanced partitioner and boot from a live-usb pen. 
I remember there was a bug where the installer selected the usb drive for installing the boot loader instead of the hard drive if you where not paying attention.
You have to manually select your hard-drive for the boot loader. In my case it would install on sdb and I manually had to select sda, else it would only boot if I left the usb-pen in the slot Because it contained the boot loader.
Maybe that's your problem ?

---

