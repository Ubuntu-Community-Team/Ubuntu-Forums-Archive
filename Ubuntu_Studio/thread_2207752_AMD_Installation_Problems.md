---
title: "AMD Installation Problems"
date: 2014-02-25
forum: Ubuntu Studio
---

### Post by country0129 on 2014-02-25
I have an AMD Athlon II X 4 635 Processor, 2.9 GHz. I've downloaded, tried to install the latest version of UbuntuStudio, choosing the AMD 64 package, but it fails on install, stating that I have the wrong processor, need the package for this machine. I was trying to install it on a Virtual Machine. Any suggestions?

---

### Post by QIII on 2014-02-25
Hello!

Have you made sure AMD-v is enabled in your BIOS? Your virtualization software will need that to be set to virtualize a 64 bit OS.

---

### Post by Yellow Pasque on 2014-02-26
Make sure you have the VM software set to virtualize a 64-bit CPU. I forget whether Virtualbox offers this setting, but I know qemu frontends do.

---

### Post by brianmc on 2014-03-03
I've had issues on Linux getting a version of VirtualBox which properly supports 64-bit guest operating systems running on Linux.
The obvious questions to ask are:

[LIST]
[*]What exact host operating system/Linux flavour are you using? 
[*]Have you verified you can install a regular 64-bit Ubuntu install? 
[*]Are you being generous with the allocated resources (CPU cores, RAM)? 
[/LIST]
As suggested above, you do need to check all the BIOS settings are correct for you to be able to run 64-bit guest OSes. You also (probably) need to download VirtualBox from Oracle to get full emulation support.

If you want to confirm the issue is VirtualBox, then my suggestion would be start by writing the 64-bit Ubuntu Studio image to a USB stick, and attempting to boot from that. If it fails, start digging into BIOS settings. Once it works, run through the above points.

---

