---
title: "Gdk-pixbuf 2.36.10-1 breaks visibility of tiff files"
date: 2017-09-20
forum: Ubuntu Development Version
---

### Post by harry332 on 2017-09-20
The package gdk-pixbuf 2.36.10-1 is in artful-proposed now.
I tried to test it and found out that after upgrading it from the release version 2.36.5-3ubuntu1 the tiff files cannot be opened no longer.
Well, downgrading back to 2.36.5-3ubuntu1 tiff files are OK again.

Here is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/gdk-pixbuf/+bug/1718526](https://bugs.launchpad.net/ubuntu/+source/gdk-pixbuf/+bug/1718526)

---

### Post by mc4man on 2017-09-20
Maybe it's from this which had a fix committed right after 2.36.10 release
[https://bugzilla.gnome.org/show_bug.cgi?id=786342](https://bugzilla.gnome.org/show_bug.cgi?id=786342)
[https://github.com/GNOME/gdk-pixbuf/commit/66537d1ecf7e857a0a443c1ebf72baf6f19dd3e4](https://github.com/GNOME/gdk-pixbuf/commit/66537d1ecf7e857a0a443c1ebf72baf6f19dd3e4)

---

### Post by harry332 on 2017-09-21
Yes in gnome.org there is a patch that fixes this.
Perhaps tomorrow we have the fixed 2.36.10-2 version in artful-proposed.

---

### Post by harry332 on 2017-09-21
The fixed version 2.36.10-2 is in artful-proposed already.

---

