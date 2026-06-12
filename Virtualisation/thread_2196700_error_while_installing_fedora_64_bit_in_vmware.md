---
title: "error while installing fedora 64 bit in vmware"
date: 2013-12-30
forum: Virtualisation
---

### Post by Raj_kishor on 2013-12-30
i get the follwring error.
This virtual machine is configured for 64-bit guest operating systems. However, 64-bit operation is not possible.
This host supports Intel VT-x, but Intel VT-x is disabled.
Intel VT-x might be disabled if it has been disabled in the BIOS/firmware settings or the host has not been power-cycled since changing this setting.
(1) Verify that the BIOS/firmware settings enable Intel VT-x and disable 'trusted execution.'
(2) Power-cycle the host if either of these BIOS/firmware settings have been changed.
(3) Power-cycle the host if you have not done so since installing VMware Workstation.
(4) Update the host's BIOS/firmware to the latest version.
For more detailed information, see [http://vmware.com/info?id=152](http://vmware.com/info?id=152).
i am a beginner plz help me thanks

---

### Post by jeffreyjensen1989 on 2013-12-30
You have to either:
A) reboot and enable VT-x which allows the virtual machine to detect a 64bit cpu 
or 
B) install a 32 bit version. 
If you don't have at least a quad core CPU I would recommend B because it wont slow down your host OS as much

---

### Post by Bucky Ball on 2013-12-30
*Thread moved to **Virtualisation**.*

---

### Post by Raj_kishor on 2013-12-30
thanks bloke. but how do i reboot and enable vt-x ??

---

