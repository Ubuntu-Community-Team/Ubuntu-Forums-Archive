---
title: "Messed up 3d after upgrade from automatix repos."
date: 2006-08-19
forum: Repositories &amp; Backports
---

### Post by Bastanteroma on 2006-08-19
I foolishly kept the automatix repos on an otherwise fresh install, then installed the 1 step xgl package and set it up as a session choice (I'm having trouble finding the post I followed, but it was recent and simple).  I logged in using xgl but things were super slow, as if 3d weren't working.  I've got an intel 915 that was previously working fine.
When I logged back in using the regular xorg I noticed that there were updates having to do with Mesa and opengl available, which I hoped might magically make things work.  Instead, when I tried to log back in using xgl I got an error message: 

i915 DRI driver expected DDX version 1-1.5.x but got version 1.4.1

followed by a series of libGL warnings.

Any ideas how to restore the original setup and repos?

---

