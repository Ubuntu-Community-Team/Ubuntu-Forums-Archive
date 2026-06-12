---
title: "Existing Gutsy install in QEMU"
date: 2008-03-30
forum: Virtualisation
---

### Post by dfreidin on 2008-03-30
I have a dual boot with Vista and Gutsy Gibbon. I've been trying to find a way to virtualize my existing install of Gutsy in Vista so that I don't have to reboot so often. (I looked at virtualizing Vista in Gutsy, but apparently there are issues with activation that I don't want to deal with.) I found out how to use QEMU to boot from my hard drive, and I can get it going with the following options:
```
-m 512 -L \QemuManager\QemuManager\qemu -hda \\.\PhysicalDrive0 -boot c
```
This boots up a virtual machine and gets me into GRUB. From there, I can start up my Gutsy install. However, once it gets past the progress bar, it says:
```
Could not start the X
Server due to some internal error.
Please contact your sysem adminstrator
or check your syslog to diagnose.
In the meantime this display will be
disabled. Please restart GDM when the
problem is corrected
```
By the way, it says that so quickly that I can barely read the first line. I found the full error message elsewhere. After that message, the QEMU screen fills with junk and locks up, so I have to just quit. My Gutsy install works just fine when I boot it normally, so I'm at a loss as to what might be the problem when using it in QEMU.

---

### Post by mvan83 on 2008-03-30
You'll need to change the xorg.conf file in the vm. The driver section will need to be changed. To what? I don't know, since 99% of my VM experience is with vmware (where the driver would be "vmware"). If you have a gutsy vm installed which runs under qemu, fire it up and see what's in the xorg.conf file there.

---

