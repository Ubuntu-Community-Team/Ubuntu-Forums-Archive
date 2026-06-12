---
title: "Latest firefox upgrade (ubp3) kills devhelp"
date: 2005-06-08
forum: Ubuntu Backports
---

### Post by infinito on 2005-06-08
The latest update on firefox backport (1.0.4-1ubuntu3~5.04ubp3), kills devhelp installation, 'cause it removes "mozilla-firefox", which is a dependencie for "libdevhelp-1-0", which is needed by devhelp and all its books.
```
infinito@soho:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  firefox-gnome-support
Suggested packages:
  latex-xft-fonts xprint
The following packages will be REMOVED:
  devhelp devhelp-book-autotools devhelp-book-binutils devhelp-book-cvs devhelp-book-emacs devhelp-book-gdb devhelp-book-glibc devhelp-book-gtk2
  devhelp-book-make devhelp-book-sdl devhelp-books gnome-devel libdevhelp-1-0 mozilla-firefox
The following packages will be upgraded:
  firefox firefox-gnome-support
2 upgraded, 0 newly installed, 14 to remove and 0 not upgraded.
Need to get 8634kB of archives.
After unpacking 13.5MB disk space will be freed.
Do you want to continue [Y/n]?
```

---

### Post by jdong on 2005-06-08
yep, see that; an extra Conflicts:. :)

I'm rebuilding using an alternate dummy package setup.

---

### Post by jdong on 2005-06-08
Newly uploaded 1.0.4-1ubuntu3~5.04ubp5 fixes this issue.

---

### Post by infinito on 2005-06-08
[QUOTE=jdong]Newly uploaded 1.0.4-1ubuntu3~5.04ubp5 fixes this issue.[/QUOTE]
 Great. Now everything's ok again. Thanks!

---

