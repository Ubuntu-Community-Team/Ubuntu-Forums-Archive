---
title: "libSDL1.2-dev repository trouble"
date: 2006-12-28
forum: Repositories &amp; Backports
---

### Post by Chimu on 2006-12-28
In attempting to install libSDL-dev to compile a game I found on the net, Synaptic reports:
> libsdl1.2-dev:
 Depends: libglu1-mesa-dev but it is not going to be installed or
	libglu-dev

Trying to install libglu1-mesa-dev reports another one of these errors, as does it's dependency.  Removing libglu1-mesa to reinstall all of this would remove 530MB of my system, including GNOME as well. How can this problem be fixed?

---

### Post by oh_noname on 2007-01-16
Aptitude is pretty good when it comes to solutions.

sudo aptitude install libsdl1.2-dev

...presented a solution to downgrade some gl-libs for me which allowed for libsdl1.2-dev to be installed.

cheers

---

