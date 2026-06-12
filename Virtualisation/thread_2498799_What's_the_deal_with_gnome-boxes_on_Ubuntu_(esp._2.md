---
title: "What's the deal with gnome-boxes on Ubuntu (esp. 24.04)?"
date: 2024-06-27
forum: Virtualisation
---

### Post by 0f4d0335 on 2024-06-27
Hi all,

I'm having trouble with my installation of gnome-boxes for Ubuntu 24.04 LTS. There doesn't appear to be much conversation about it, but I can confirm personally that this issue followed me from 22.04 LTS. :(

The issue isn't something I can show with a screen shot. The VM container will open its installer and start the VM. But then soon after the block turns black. If I wait or try restarting the container, the graphics may open but typically freeze until sometime has passed. When it doesn't freeze, it works perfectly fine like it does for me on Debian.

Can I do anything that is known to improve the service?

What I've done is set my Power Mode from Balanced to Performance. 

Thanks. ):P

---

### Post by slovenskekasina on 2024-08-06
Update System and Drivers and install Latest QEMU and Libvirt, then enable 3D Acceleration

---

