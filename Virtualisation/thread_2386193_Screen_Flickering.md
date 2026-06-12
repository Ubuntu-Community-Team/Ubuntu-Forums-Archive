---
title: "Screen Flickering"
date: 2018-03-02
forum: Virtualisation
---

### Post by zliu113 on 2018-03-02
Hello,

I just installed Ubuntu 17.10. However, the screen keeps flickering, Could you please help with it?
```

zhaonan@zhaonan-VirtualBox:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.10
DISTRIB_CODENAME=artful
DISTRIB_DESCRIPTION="Ubuntu 17.10"
zhaonan@zhaonan-VirtualBox:~$ uname -a
Linux zhaonan-VirtualBox 4.13.0-36-generic #40-Ubuntu SMP Fri Feb 16 20:07:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
zhaonan@zhaonan-VirtualBox:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter [80ee:beef]
	Kernel driver in use: vboxvideo
	Kernel modules: vboxvideo
zhaonan@zhaonan-VirtualBox:~$ env | grep DESK
DESKTOP_SESSION=ubuntu
XDG_SESSION_DESKTOP=ubuntu
XDG_CURRENT_DESKTOP=ubuntu:GNOME
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
```

---

### Post by ajgreeny on 2018-03-02
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

---

### Post by cruzer001 on 2018-03-02
Hello

First thing to do, switch to xorg:
[https://itsfoss.com/switch-xorg-wayland/](https://itsfoss.com/switch-xorg-wayland/)

About vBox:
Most people find that vBox 5.2 works better with the 17.10 kernel.
Have you installed extension pack/guest additions?
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

I find a big performance difference by running 2vCPUs and a minimum of 2G ram, 3G is better.

Test your guest without 3D enabled and set your video ram at the max (128M).

---

