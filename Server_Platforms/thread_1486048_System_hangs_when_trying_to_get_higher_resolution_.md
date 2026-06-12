---
title: "System hangs when trying to get higher resolution than 640x480"
date: 2010-05-17
forum: Server Platforms
---

### Post by *Happy* on 2010-05-17
Hi,
I have just installed Ubuntu Server 10.04. With Version 8.04 I had no problem to change the resolution from 640x480 to 1440x900 (console, no GUI installed). With 10.04, it does not work, the only resolution that works is 640x480.

I have tried the following:

Changed: GRUB_GFXMODE=1440x900
Result: Success, Grub comes up with 1440x900, but when booting, the resolution changes to 640x480

Changed: GRUB_GFXPAYLOAD_LINUX=1440x900
Result: Booting -> blank screen > automatic reboot

Changed: GRUB_GFXPAYLOAD_LINUX=keep
Result: Booting -> blank screen > automatic reboot

Changed: Disabled Kernel Mode Setting (KMS): GRUB_CMDLINE_LINUX="nomodeset"
Result: Booting -> blank screen > automatic reboot

Changed: GRUB_PRELOAD_MODULES=vbe
Result: Booting -> blank screen > automatic reboot

Changed: GRUB_CMDLINE_LINUX="vga=0x16b" (worked in 8.04)
Result: No effect

The system runs as VMWare virtual machine and has no 3D Acceleration.
What else can I try to get the resolution higher than 640x480?

---

### Post by *Happy* on 2010-05-18
Any suggestions?

---

### Post by *Happy* on 2010-05-19
Solution:

1, removed vesafb from blacklist
2. added vga16fb to blacklist

Now I have the desired resolution 1440x900.

---

### Post by VcDeveloper on 2010-10-29
> ***Happy* said:**
> Solution:

1, removed vesafb from blacklist
2. added vga16fb to blacklist

Now I have the desired resolution 1440x900.

I'm trying to do the same thing, but with VBox and was [unsuccessful going through these posts]("http://ubuntuforums.org/showthread.php?p=10042314#post10042314") (see my post at the end).

Would you mind posting a step by step list in what you did to successfully change the resolution?  I would appreciate it...

---

### Post by VcDeveloper on 2010-10-29
actually peacing together all the post I've read I did this:


[LIST=1]
[*]edit /etc/modprobe.d/**blacklist-framebuffer**
[*]comment out #**blacklist vga16fb**
[*]add this **blacklist vga16fb**
[*]edit /etc/initramfs-tools/**modules**
[*]added **vga16fb**
[*]run **update-initramfs -u**
[*]edit /etc/default/**grub**
[*]modified GRUB_GFXMODE=**1024x768**
[*]run **update-grub2**
[/LIST]
  
...BUT, I had to add this **vga=773**  at the boot prompt menu by editing args.  So I successfully running in a desired resolution.

....so my question is, where is this menu with the args to I can  manually add this so I don't have to keep doing this at boot time?

---

### Post by VcDeveloper on 2010-10-29
Actually, I discovered all I had to do is add the vga=773 to the /boot/grub/grub.cfg:

kernel /boot/vmlinuz-2.6.35.6-46.fc14.i686...... ro vga=773 quiet

This file displays the boot menu.

---

