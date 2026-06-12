---
title: "Incompatible Ricotz Testing and Gnome3 Team PPA's"
date: 2012-01-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-01-09
A warning here for those, who use both Ricotz Testing PPA (for Gnome-shell) and Gnome3 Team PPA (for Gnome 3).

Today Gnome3 Team uploaded into the PPA an older mutter than there already was uploaded into the Ricotz Testing PPA.
Gnome3 Team mutter uses libcogl5, while Ricotz Testing PPA uses libcogl6.
These should not be installed together.

Now this is funny because Ricotz Testing PPA recommends people the Gnome3 Team PPA. :D

---

### Post by jbicha on 2012-01-10
Good catch. I didn't realize Ricotz's cogl had a soname bump (to libcogl6). I won't be able to fix this right now though.

By the way, for those using just the GNOME 3 PPA, you need to upgrade mutter and gnome-shell together. It looks like gnome-shell will take several more hours to build. Maybe I should have used a staging PPA to reduce the time where things are broken while waiting to build. It's a WIP and you may need to wait a couple days for everything to get straightened out.

---

### Post by Harry33 on 2012-01-10
This issue is now solved.
There are new mutter and cogl packages with correct dependencies in the Gnome3 Team PPA now.
Also, Ricotz Testing PPA has now newer git-version of the mutter and gnome-shell.

---

