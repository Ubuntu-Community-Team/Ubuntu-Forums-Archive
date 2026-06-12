---
title: "Nouveau 3D in Ubuntu?"
date: 2009-12-22
forum: The Cafe
---

### Post by Qola on 2009-12-22
Is it possible? I know there are packages available for OpenSUSE.

---

### Post by orlox on 2009-12-22
From the nouveau wiki

> 
3D support is worked on using Gallium3D and can (depending on the Chip generation and the applications) be quite usable, butAt the moment, the nv50 (GeForce 8 and up) gallium driver can actually run compiz to some extent already. There's some minor graphical issues, but it works. still officially considered experimental.
In October 2009, Ben Skeggs improved the nv50 (GeForce 8 and up) Gallium3D driver to actually run compiz to some extent. There are some minor graphical issues, but it works.
As of December 2009 the nv40 Gallium3D driver runs compiz, again with minor graphical issues.


The ubuntu packages don't have 3d support, and I don't know if the xorg-edgers ppa has them...But the wiki confirms what you say, there are openSUSE packages with 3d enabled.

---

### Post by gnomeuser on 2009-12-22
I would wager that if this is going to be testable for Ubuntu then we'd see it phased in via the xorg-edgers ppa (this really is a dangerous undertaking - use with the utmost of care and learn to love ppa-purge before enabling it).

---

