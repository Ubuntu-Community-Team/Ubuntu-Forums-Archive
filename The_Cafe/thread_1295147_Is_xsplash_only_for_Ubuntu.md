---
title: "Is xsplash only for Ubuntu ?"
date: 2009-10-19
forum: The Cafe
---

### Post by praveesh on 2009-10-19
Does kUbuntu has xsplash ?

---

### Post by miegiel on 2009-10-19
> **praveesh said:**
> Does kUbuntu has xsplash ?

Xubuntu (9.10 karmic) has it. I'm pretty sure kubuntu has it too, though only since karmic.

[http://packages.ubuntu.com/search?keywords=xsplash&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=xsplash&searchon=names&suite=all&section=all)

---

### Post by praveesh on 2009-10-19
> **miegiel said:**
> Xubuntu (9.10 karmic) has it. I'm pretty sure kubuntu has it too, though only since karmic.

[http://packages.ubuntu.com/search?keywords=xsplash&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=xsplash&searchon=names&suite=all&section=all)

thanks . But in your link, only Ubuntu -xsplash-artwork could be found . No kUbuntu-xsplash-artwork

---

### Post by miegiel on 2009-10-19
> **praveesh said:**
> thanks . But in your link, only Ubuntu -xsplash-artwork could be found . No kUbuntu-xsplash-artwork

In Xubuntu xsplash depends on *ubuntu-xsplash-artwork* so that might mean the artwork for xubuntu's xsplash is in that package. Or the stuff I'm seeing here during boot isn't xslpash :roll: Maybe you can find more info in the [_karmic testing sub forum_]("http://ubuntuforums.org/forumdisplay.php?f=359").

```
user@machine:~$ sudo aptitude show xsplash
Package: xsplash
New: yes
State: installed
Automatically installed: no
Version: 0.8.4-0ubuntu1
Priority: optional
Section: misc
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 98.3k
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.3.6-6~), libcairo2 (>= 1.2.4),
         libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>=
         2.4.0), libfreetype6 (>= 2.2.1), libglib2.0-0 (>= 2.16.0), libgtk2.0-0
         (>= 2.14.0), libpango1.0-0 (>= 1.14.0), libxcomposite1 (>= 1:0.3-1),
         ubuntu-xsplash-artwork | xsplash-artwork
Description: X based bootsplash
 xsplash is a userspace application that uses the X interface to draw a splash
 screen at boot.
Homepage: https://launchpad.net/xsplash
```

---

### Post by praveesh on 2009-10-19
> **miegiel said:**
> In Xubuntu xsplash depends on *ubuntu-xsplash-artwork* so that might mean the artwork for xubuntu's xsplash is in that package. Or the stuff I'm seeing here during boot isn't xslpash :roll: Maybe you can find more info in the [_karmic testing sub forum_]("http://ubuntuforums.org/forumdisplay.php?f=359").

```
user@machine:~$ sudo aptitude show xsplash
Package: xsplash
New: yes
State: installed
Automatically installed: no
Version: 0.8.4-0ubuntu1
Priority: optional
Section: misc
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 98.3k
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.3.6-6~), libcairo2 (>= 1.2.4),
         libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>=
         2.4.0), libfreetype6 (>= 2.2.1), libglib2.0-0 (>= 2.16.0), libgtk2.0-0
         (>= 2.14.0), libpango1.0-0 (>= 1.14.0), libxcomposite1 (>= 1:0.3-1),
         ubuntu-xsplash-artwork | xsplash-artwork
Description: X based bootsplash
 xsplash is a userspace application that uses the X interface to draw a splash
 screen at boot.
Homepage: https://launchpad.net/xsplash
```

Thanks

---

