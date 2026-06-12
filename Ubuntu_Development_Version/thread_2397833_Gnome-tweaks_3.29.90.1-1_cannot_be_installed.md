---
title: "Gnome-tweaks 3.29.90.1-1 cannot be installed"
date: 2018-08-04
forum: Ubuntu Development Version
---

### Post by harry332 on 2018-08-04
Gnome-tweaks 3.29.90.1-1 cannot be installed because of unmet dependencies.
This new version of gnome-tweaks is in proposed right now.
It depends on gir1.2-glib-2.0 (>=2.57.2). However only version 1.56.1-1 is available. [URL="https://launchpad.net/ubuntu/cosmic/amd64/gir1.2-glib-2.0"]

[/URL]

---

### Post by Frogs Hair on 2018-08-04
I would suggest waiting, missing or held packages can be part of using the proposed repository  especially on a development release.

---

### Post by harry332 on 2018-08-07
Well todays update to gobject-introspection (1.57.2-2) did not help at all.
There must be a bug in gnome-tweaks v. 3.29.90.1-1 as it depends on gir1.2-glib-2.0 (>=2.57.2). We have now 1.57.2-2 in proposed!

---

### Post by harry332 on 2018-08-07
Here is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/gnome-tweaks/+bug/1785858](https://bugs.launchpad.net/ubuntu/+source/gnome-tweaks/+bug/1785858)

---

### Post by PaulW2U on 2018-08-08
Dependency fixed and migrated out of proposed.

Check the changelog harry332. You got a mention. ;)

---

### Post by harry332 on 2018-08-09
Yes, this bug is fixed:
updated version 3.29.90.1-2

---

