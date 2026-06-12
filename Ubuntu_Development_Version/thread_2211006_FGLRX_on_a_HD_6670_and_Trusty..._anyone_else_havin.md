---
title: "FGLRX on a HD 6670 and Trusty... anyone else having problems?"
date: 2014-03-13
forum: Ubuntu Development Version
---

### Post by Sslaxx on 2014-03-13
When I upgraded to Trusty beta, X would refuse to start (it crashed with a hard lock-up). I had to remove the FGLRX drivers to get it to work. Anyone else experienced this issue?

---

### Post by QIII on 2014-03-13
Hello!

If you upgraded your version (as opposed to a clean install) without first uninstalling all proprietary drivers (especially the graphics driver), that could be the problem.

Upgrading versions without uninstalling proprietary drivers is a frequent cause of significant emotional events.

If things are all settled now, you might try to reinstall the fglrx driver.

---

### Post by Sslaxx on 2014-03-29
It works now, but it seems to make little to no difference to 3D performance.

---

### Post by monkeybrain20122 on 2014-03-29
> **Sslaxx said:**
> It works now, but it seems to make little to no difference to 3D performance.

Because the open driver is getting very good. I read that its 3d performance is catching up with fglrx and its 2d performance is actually better. You may need fgrlx for higher fps and opengl versions but otherwise I would just use the open driver, works out of the box and no headaches with kernel update etc.

---

### Post by Sslaxx on 2014-03-29
> **monkeybrain20122 said:**
> Because the open driver is getting very good. I read that its 3d performance is catching up with fglrx and its 2d performance is actually better. You may need fgrlx for higher fps and opengl versions but otherwise I would just use the open driver, works out of the box and no headaches with kernel update etc.
With (for example) OpenMW, I've noticed no practical difference between the FGLRX drivers and the open source ones.

---

