---
title: "Unable to access any TTY console"
date: 2013-05-08
forum: Ubuntu Development Version
---

### Post by slickymaster on 2013-05-08
So, today I wake up not being able to access any TTY console. Ctrl+Alt+F[1-6] is just not working, just open up a completely black screen.

I tried to switch to true text-mode by configuring Grub, assuming the graphical text-mode resolution set at boot wasn't compatible with my video card.
```
sudo sed -i -e 's/#GRUB_TERMINAL/GRUB_TERMINAL/g' /etc/default/grub
sudo update-grub
```
But nothing.

Here's some info:
```
lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
3.9.0-030900rc3-generic
```


```
lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter [80ee:beef]
```

---

### Post by slickymaster on 2013-05-08
Fixed.

Being a perfect idiot, I forgot to reboot after switching to true text-mode and updating Grub. Rebooted and now I recovered the access all TTY consoles.

---

