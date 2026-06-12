---
title: "How to access desktop effects settings"
date: 2013-03-05
forum: Virtualisation
---

### Post by puraki on 2013-03-05
I am running an Ubuntu 12.04.1 LTS 32-bit system in VirtualBox 4.1.16 on Windows 7 64-bit. However, when I click on the Unity dash (or press the Windows/Super key), the dash doesn't fade in. How can I access the desktop effects settings in Ubuntu?

---

### Post by TheFu on 2013-03-06
Advanced graphics "cheese" is a bad idea inside a virtual machine.  In fact, I refuse to run Unity inside a VM. LXDE or XFCE are better choices for me.

If you insist on using the "cheese," be certain to provide the client OS the max video RAM, enable 3D GPU accel in the VM clientOS settings and install the guest additions.

---

### Post by puraki on 2013-03-06
I have gave the VM the maximum amount of video RAM, enabled 3D acceleration in the settings, and I have installed the guest additions on it, but the problem is still there.

---

