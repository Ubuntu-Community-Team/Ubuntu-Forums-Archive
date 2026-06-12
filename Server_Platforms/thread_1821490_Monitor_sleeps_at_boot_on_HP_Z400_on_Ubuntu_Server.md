---
title: "Monitor sleeps at boot on HP Z400 on Ubuntu Server"
date: 2011-08-09
forum: Server Platforms
---

### Post by abc1987 on 2011-08-09
Hi there,

I am trying to configure Ubuntu Server on an HP Z400 workstation (without X) but am encountering an issue where on boot the monitor is automatically put into sleep mode. This does not happen during setup, but rather after installation when the computer reboots and has passed through GRUB. I have tried to access Recovery Mode to no avail.

The issue occurs on both Ubuntu Server 10.04 LTS and 11.04 (I switched to 11.04 in the hope newer packages would correct the problem). The graphics card is an nVidia NVS 300. Once the system is configured it will likely be managed via SSH but the built-in graphics should provide a fallback.

I notice that the HP Z400 is Ubuntu-certified, but I assume this applies to the desktop version only.

Does anyone have any idea what is likely to be the cause of this issue and how it can be resolved? Thanks.

---

### Post by gobbledigook on 2011-08-09
are you sure the monitor is asleep? 

the server edition on ubuntu is designed for headless machines... so after grub you should be greeted with a login prompt?

which cable are you using to connect the monitor... should be no problem with VGA

---

