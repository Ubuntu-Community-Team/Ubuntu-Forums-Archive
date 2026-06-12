---
title: "Request: GTK+2.2 or higher"
date: 2005-05-07
forum: Ubuntu Backports
---

### Post by Psquared on 2005-05-07
Can GTK+2.2 be backported to Hoary. (I tried to see if its Breezy, but I could not tell) I think its called libgtk+ in Ubuntu. Hoary seems to be using 2.0 (actually 1.95) but GTK.org is actually up to stable version 2.6.7.

The reason i want it is for rox-filer and rox-sessions. The full-blown DE looks really cool and logical. It is completely non-windows and is based on folders/directories instead of the windows like menus that Gnome, KDE and Xfce have gone to. It can be run with any WM and most programs are compatible with it because it uses the Linux kernel.

What say you? :D

---

### Post by JonahRowley on 2005-05-08
```
$ apt-cache show libgtk2.0-0
```
Hoary is using 2.6.4-0ubuntu3.  I think what you need (you're building from source, right?) is **apt-get install libgtk2.0-dev**.

---

### Post by Psquared on 2005-05-08
[QUOTE=JonahRowley]```
$ apt-cache show libgtk2.0-0
```
Hoary is using 2.6.4-0ubuntu3.  I think what you need (you're building from source, right?) is **apt-get install libgtk2.0-dev**.[/QUOTE]

Thanks. How did you find that out? I wonder why Ubuntu calls it 2.0?

Yes, I'm compiling from source so now I'll give it a try and see if that does it.

Thanks again.

---

### Post by jdong on 2005-05-08
2.6.4 is considered to be a point release [aka minor revision] to GTK+ 2.0.

1.0 and 2.0 are slotted (installed side-by-side as opposed to 1.0 upgrading to 2.0), because both are still in use today.

---

### Post by Psquared on 2005-05-09
[QUOTE=jdong]2.6.4 is considered to be a point release [aka minor revision] to GTK+ 2.0.

1.0 and 2.0 are slotted (installed side-by-side as opposed to 1.0 upgrading to 2.0), because both are still in use today.[/QUOTE]

Thanks. I needed the -dev packages anyway. Once I got them the program compiled fine.

---

