---
title: "Option to install SATA/RAID during setup"
date: 2008-04-14
forum: Ubuntu Brainstorm
---

### Post by SonicSteve on 2008-04-14
The idea is simple and anyone who as ever installed Windows XP or Vista on a RAID enabled mainboard knows what I'm suggesting already.

Recently I tested Ubuntu on a high end Asus workstation mainboard. It failed miserably much to my disappointment. The reason it failed is that the mainboard uses a marvel raid controller which Ubuntu didn't like. This board (P5E-ws-pro) had linux source code drivers on it's CD which could have been used. Windows won't install on this board either unless you use the "Press F6 to install third party drivers" option right at the very beginning of setup. Without doing this Windows will blue screen and fail also.

I'm proposing that Ubuntu adds a component to the setup that behaves like the F6 option that Windows has. This option would read from a USB drive or CD or.... and compile the drivers into the setup so that the drivers will be available during setup.

There are many boards out there that use RAID controllers, and not all of them are supported by the default Linux Kernel. Also most users are not experienced enough to be able to compile a custom kernel, let alone get past the setup error of the kernel not recognizing the RAID controller. 

I don't know how useful the Ubuntu Brainstorm site is but here is a link to the idea posted there.

[http://brainstorm.ubuntu.com/idea/7011/](http://brainstorm.ubuntu.com/idea/7011/)

---

