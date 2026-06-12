---
title: "Password elimination"
date: 2010-12-18
forum: Security
---

### Post by Historynut on 2010-12-18
I have two hard drives in my computer; one for Ubuntu and the other Windows XP. When I want to access files using Ubuntu from the Windows hard drive, I must enter a password. Is there any  way of eliminating this? If not, is there any way of placing the Windows file (C) as an icon on the Ubuntu desktop? Once I access it, the drive (C) is on the desktop so that I can go to it with no problem, but it disappears when the machine is turned off.

---

### Post by cariboo on 2010-12-18
What version are you using? Since Lucid at least you don't need a password to access an NTFS partition. To mount your WIndows partition automagically on boot, you can use something similar to this in /etc/fstab:

```
/dev/sdxX  /<mountpoint>  ntfs-g3  defaults  0  0
```

Where /dev/sdXx = you Windows partition and <mountpoint> = where you have the Windows partition mounted.

If you don't what to get your hands dirty, working in a terminal, you can install ntfs-config from the repositories, and do the same thing in a gui.

---

