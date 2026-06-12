---
title: "QQ and Gnome = broken on last updates"
date: 2012-07-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by sammiev on 2012-07-04
Looks like a little bug with Gnome3 this morning. All others working good. :)

---

### Post by Harry33 on 2012-07-04
Gnome-panel (part of Gnome3) works just fine.
However gnome-shell is broken due to broken folks package.

So, do not upgrade packages gir1.2-folks-0.6 and libfolks25.
The version broken is 0.7.2.2-0ubuntu1,
version 0.6.9-1build1 works fine.

---

### Post by dbloom on 2012-07-04
> **Harry33 said:**
> Gnome-panel (part of Gnome3) works just fine.
However gnome-shell is broken due to broken folks package.

So, do not upgrade packages gir1.2-folks-0.6 and libfolks25.
The version broken is 0.7.2.2-0ubuntu1,
version 0.6.9-1build1 works fine.

how do we revert back to the previous version? Thanks!

EDIT: ok, i just realized what QQ meant -- i guess i'm on PP with a gnome shell issue.  Also, my version of gir1.2-folks is 0.6.8-2.  i suspect something else is breaking gnome shell since both PP and QQ are affected.  must be a common update...

i'm on a 64bit setup with AMD quadcore and nvidia cards running beta drivers. it seems like all compositing (unity and gs) are broken for me.

---

### Post by dino99 on 2012-07-04
> **Harry33 said:**
> Gnome-panel (part of Gnome3) works just fine.
However gnome-shell is broken due to broken folks package.

So, do not upgrade packages gir1.2-folks-0.6 and libfolks25.
The version broken is 0.7.2.2-0ubuntu1,
version 0.6.9-1build1 works fine.

i have those working nicely here on i386, but with gtk3 & glib2 from ricotz/testing ppa

---

### Post by Harry33 on 2012-07-04
> **dino99 said:**
> i have those working nicely here on i386, but with gtk3 & glib2 from ricotz/testing ppa

What version of folks are you using now, 0.7.2.2-0ubuntu1?

---

### Post by dino99 on 2012-07-04
> **Harry33 said:**
> What version of folks are you using now, 0.7.2.2-0ubuntu1?

0.7.2.2-0ubuntu1 with gtk-3 3.5.7~git20120702 & glib-2 1.33.4~git20120702

gtk-3 & glib-2 packages are updated from ricotz/testing, but not the other packages from this ppa.

---

### Post by Harry33 on 2012-07-04
> **dino99 said:**
> 0.7.2.2-0ubuntu1

Right, so you must also be using the Ricotz version of gnome-shell (3.5.3+git) which has been built against the new evolution-data-server (3-5-3-1).

---

### Post by dino99 on 2012-07-04
> **Harry33 said:**
> Right, so you must also be using the Ricotz version of gnome-shell (3.5.3+git) which has been built against the new evolution-data-server (3-5-3-1).

no, i only have gnome-classic installed here on i386, no g-s or unity (but evolution has been upgraded too from quantal-proposed)

---

### Post by sammiev on 2012-07-04
Fixed after tonights updates. :)

---

### Post by Harry33 on 2012-07-05
Right, the version 0.7.2.2-0ubuntu2 works.

---

