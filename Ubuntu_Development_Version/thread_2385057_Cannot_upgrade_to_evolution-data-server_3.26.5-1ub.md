---
title: "Cannot upgrade to evolution-data-server 3.26.5-1ubuntu2"
date: 2018-02-15
forum: Ubuntu Development Version
---

### Post by harry332 on 2018-02-15
I have the proposed repo enabled.

Just noticed that if I try to upgrade to the newest evolution-data-server (in proposed now) and specifically the package libecal-1.2-19, gnome-shell will be removed.
This happens even though I am using the newest gnome shell 3.26.2-0ubuntu3 (also in proposed now).

And the reason is this:
The package libecal-1.2-9 conflicts << gnome-shell 3.26.2-1+b1.

We need a newer gnome-shell now.

---

### Post by dino99 on 2018-02-15
Same here; i suppose the upgrade is not yet complete, or some packages need a rebuilt; keep waiting a bit to a self fix.

---

### Post by dino99 on 2018-02-15
A new version has solved the upgrade issue.

---

### Post by harry332 on 2018-02-16
Yes the update evolution-data-server 3.26.5-1ubuntu3 did solve this issue.

---

