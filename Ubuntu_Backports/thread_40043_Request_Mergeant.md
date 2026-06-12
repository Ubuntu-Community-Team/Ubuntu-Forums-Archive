---
title: "Request: Mergeant"
date: 2005-06-07
forum: Ubuntu Backports
---

### Post by webwurst on 2005-06-07
[http://packages.ubuntu.com/breezy/gnome/mergeant](http://packages.ubuntu.com/breezy/gnome/mergeant)

the version in hoary seems to be quite old: 0.12.1
in breezy there is: 0.52 (released august-2004)

version 0.60 is just released: [http://www.gnomefiles.org/app.php?soft_id=199](http://www.gnomefiles.org/app.php?soft_id=199)

---

### Post by jdong on 2005-06-07
Well, I'll bring you up-to-date with Breezy.

Forced a build against Hoary deps, despite how libgda2 and libgnomedb2 are 1.1.99 (when 1.2 is needed).

---

### Post by webwurst on 2005-06-30
thx for your effort!

but unfortunately the backport didn't work very good for me ..
it chrashed here and there (somtimes on connecting to a database or after a working connection on reading in the database-structure).

for now i use mergeant-0.6 compiled from source.

---

