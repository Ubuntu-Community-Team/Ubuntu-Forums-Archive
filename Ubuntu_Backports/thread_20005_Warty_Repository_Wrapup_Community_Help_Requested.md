---
title: "Warty Repository Wrapup: Community Help Requested"
date: 2005-03-14
forum: Ubuntu Backports
---

### Post by jdong on 2005-03-14
Well, we have around 50 packages 'staging' at the moment, that I'd like to get out of there. There's two options for these packages:

1. Promote them

2. Delete them


I need you guys to help me choose. Currently, there's three files in the repository:

Those unfiled: [http://backports.ubuntuforums.org/backports/warty.staging](http://backports.ubuntuforums.org/backports/warty.staging)

Those to be promoted: [http://backports.ubuntuforums.org/backports/warty.promote](http://backports.ubuntuforums.org/backports/warty.promote)

And those to be removed: [http://backports.ubuntuforums.org/backports/warty.remove](http://backports.ubuntuforums.org/backports/warty.remove)

---

### Post by kassetra on 2005-03-14
The bluefish package, definitely needs to be promoted (as it's listed), also, I believe these work just fine and also should be promoted:

gaim* 1.1.2
beep-media-player* 0.9.7 & bmp-extra-plugins

....

libglib2 works fine, technically... but it has an odd menu issue that I do not if it's been resolved yet or not.

---

### Post by dcstar on 2005-03-15
[QUOTE=kassetra]
.......
libglib2 works fine, technically... but it has an odd menu issue that I do not if it's been resolved yet or not.[/QUOTE]
Since that libglib2 is also a dependency for things like the latest Firefox backport, it complicates things a bit for those if us that still can't use it.......

---

### Post by kassetra on 2005-03-15
[QUOTE=dcstar]Since that libglib2 is also a dependency for things like the latest Firefox backport, it complicates things a bit for those if us that still can't use it.......[/QUOTE]

Unless you have customized menus, libglib2 works fine...

---

### Post by dcstar on 2005-03-16
[QUOTE=kassetra]Unless you have customized menus, libglib2 works fine...[/QUOTE]
Exactly!      :sad:

---

