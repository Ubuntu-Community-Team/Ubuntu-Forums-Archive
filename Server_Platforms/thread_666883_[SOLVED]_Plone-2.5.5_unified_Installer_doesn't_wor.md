---
title: "[SOLVED] Plone-2.5.5 unified Installer doesn't work correctly"
date: 2008-01-13
forum: Server Platforms
---

### Post by datakid on 2008-01-13
The Plone 2.5.5 Unified Installer doesn't work correctly. It seems to finish, and you can see the ZMI, but you cannot add a Plone Site.

The installer can be found here:
[http://plone.org/products/plone/releases/2.5.5](http://plone.org/products/plone/releases/2.5.5)

While Plone 3.x is the latest release of plone, when supporting or developing for the older version, you may need the most up to date installer.

Gutsy/synaptic only has 2.5.2-unbuntu1 or something.

Any ideas?

---

### Post by datakid on 2008-01-13
[http://dev.plone.org/plone/ticket/5935#comment:2](http://dev.plone.org/plone/ticket/5935#comment:2) is the solution.

---

### Post by datakid on 2008-01-13
Which actually fails, since its a patch on the plone3 installer, not the plone2.5.5 installer.

---

### Post by datakid on 2008-01-13
But it does work if you insert it into line 456 of the 2.5.5 installer instead of line 322

---

