---
title: "Display Doctor 7 Beta won't install :("
date: 2008-04-29
forum: Virtualisation
---

### Post by Wake Rider on 2008-04-29
I have installed Windows 98 in VirtualBox and the graphics are piss-poor, 640 x 480 16 colours. I have read on the internet to install Display Doctor 7 beta. It will not install. It comes up with, "An I/O error occurred while installing a file. This is normally caused by bad installation media or a corrupt installation file." I click retry and it comes up again. If I click abort, it exits the installation with this message, "Corrupt installation file!" Please don't tell me to install VirtualBox Addons, I have already told that and have found out that Windows 98 does not support them. 

I tried installing Display Doctor 6.53, it installed but it wouldn't alter the graphics. I've been working on this for a few nights now, with little progress. Help!!

---

### Post by FredB on 2008-04-29
Try KVM if you have an intel-vt or amd-v enabled CPU.

Also, Windows 98 is kinda dead nowadays :(

---

### Post by Wake Rider on 2008-04-29
I have found nvidia drivers for Windows 98. However, the installation fails because it "cannot detect any nvidia chip on your system" How do I configure virtual box to have Windows 98 see my Nvidia Geforce 8600 GT 512Mb graphics card?

---

### Post by Wake Rider on 2008-04-29
I have finally managed to install it, however the registration won't work! Does anyone have the Name and Registration code for the Display Doctor Beta 7 that actually works? [ftp://ftp.scitechsoft.com/sdd/regcodes.txt](ftp://ftp.scitechsoft.com/sdd/regcodes.txt) These don't seem to work.

---

### Post by agent8131 on 2008-04-29
> **Wake Rider said:**
> I have found nvidia drivers for Windows 98. However, the installation fails because it "cannot detect any nvidia chip on your system" How do I configure virtual box to have Windows 98 see my Nvidia Geforce 8600 GT 512Mb graphics card?

You can't.  There is no way currently for the virtual system to "see" your graphics card directly.

---

