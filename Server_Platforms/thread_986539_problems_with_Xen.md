---
title: "problems with Xen"
date: 2008-11-18
forum: Server Platforms
---

### Post by adonis28850 on 2008-11-18
hi people, i have attempted to install Xen reading this tutorial:

[http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-8.04-server-install-xen-from-ubuntu-repositories)

install all, configure it, reboot, and i choose xen kernel, but when all "seems" to be loaded ok (not wifi connection) screen turns black ,and i cant do nothing, neither change to another terminal (ctrl+alt+f2), some idea??? thanks

---

### Post by adonis28850 on 2008-11-19
please some idea???:confused:

---

### Post by quad3d@work on 2008-11-23
Your video driver does not play nicely with Xen. I would disable GDM, install FreeNX and manage your Xen "server" this way. If you are trying out Xen on your desktop/laptop... you won't be able to use GUI this way.



Reboot, in GRUB boot into level 3.

Disable GDM on boot.
[http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/](http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/)

Install FreeNX
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by adonis28850 on 2008-11-23
thanks quad3d@work, but i did another one thing...i have installed debian etch instead of my long used ubuntu (debian was my first option 3 years ago when i buyed the lap-top, but you know that ubuntu supports better new laptop hardware so..), then i installed Xen on it,and... all is OK! 

the only one problem is that i must make a wired connection cause wifi connection does not work :S

---

### Post by Philio on 2008-11-23
I guess it depends on your use, but it's a lot easier just to install the latest XenServer Express from Citrix.

[http://www.citrix.com/English/ps2/products/subfeature.asp?contentID=1681151](http://www.citrix.com/English/ps2/products/subfeature.asp?contentID=1681151)

The XenCenter software is great too, only runs on Windows though unfortunately.

---

### Post by quad3d@work on 2008-11-23
> **adonis28850 said:**
> the only one problem is that i must make a wired connection cause wifi connection does not work :S

Majority of the wifi devices do not support proper bridging. Search around...

You could check out Proxmox, not Xen but uses OpenVZ+KVM. It uses a nice web front end. Only thing I found is it can't live migrate Linux, live migrate of Windows guests works though.

---

