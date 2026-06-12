---
title: "Inreasing screen resolution"
date: 2012-03-12
forum: Virtualisation
---

### Post by rmcellig on 2012-03-12
I am running Arch Linux latest version in Virtualbox 4.1.8 on my laptop which is running Zorin 4. When I go full screen, Arch Linux does not take up the entire screen. I have the latest guest additions installed as well. Any thoughts on how I can make the Arch Linux window bigger so that I can see it better.

---

### Post by TE7 on 2012-03-12
Try this:

[http://ubuntuforums.org/showthread.php?t=1940045](http://ubuntuforums.org/showthread.php?t=1940045)

---

### Post by Cheesemill on 2012-03-13
Make sure that you have installed the guest additions using Arch's own package instead of the one supplied with VirtualBox:
```
pacman -S virtualbox-archlinux-additions
```
and then add the following modules to /etc/rc.conf
```
MODULES=(... vboxguest vboxsf vboxvideo)
```

[https://wiki.archlinux.org/index.php/Virtualbox](https://wiki.archlinux.org/index.php/Virtualbox)

---

