---
title: "Mythtv Udisks Dependency"
date: 2015-09-08
forum: Ubuntu Development Version
---

### Post by PilotPaul on 2015-09-08
mythtv-frontend depends on udisks to install - this now fails since udisks has been replaced by udisks2.  Anyone any idea how I can override/rename this dependency, or does it need to go back to the mythtv devs?

---

### Post by PilotPaul on 2015-09-08
Raised as ticket #12500 in mythtv trac - target is mythtv 0.28 (currently in development).

Note that mythtv-frontend can be installed as a workaround by downloading the .deb file and installing using dpkg --ignore-depends=udisks flag.  (udisks is not needed for basic functionality)

---

### Post by dino99 on 2015-09-08
needs to be recompiled with udisks2; or set back udisk into the archive
it can be downloaded from [https://launchpad.net/ubuntu/+source/udisks](https://launchpad.net/ubuntu/+source/udisks)
and then installed via 'sudo dpkg -i packagename'

---

### Post by PilotPaul on 2015-09-10
For info: the dependency has been downgraded to "recommends" in the latest fix release for 0.27 and a task added to rewrite the udisks dependent code to incorporate udisks2 in 0.28 (currently in dev), so at least now the frontend can be installed under 15.10.  There may be an impact in detecting and playing local CD/DVD devices but everything else seems to work fine.

---

