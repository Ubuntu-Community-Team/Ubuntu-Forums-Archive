---
title: "invisable mouse in Ubuntu"
date: 2017-07-02
forum: Virtualisation
---

### Post by boodstir on 2017-07-02
I'm using Oracle Virtualbox 5.1.22 with Ubuntu 14.04.5.  All was well until I installed the Virtualbox extension pack (not the guest package).  I installed the correct pack for the Virtualbox I'm running (5.1.22 r115126).  Now when I open Virtualbox, everything is fine.  When I power on Ubuntu, I lose the mouse immediately.  It's totally invisible but it's there because when I physically move my mouse around I can see things being affected, but it's invisible inside and outside Ubuntu.  I have no option but to press the power button on my computer to shut down.  Dead in the water.

---

### Post by wildmanne39 on 2017-07-02
*Thread moved to **Virtualisation**.*

---

### Post by lammert-nijhof on 2017-07-04
Try re-installing the guest additions, since it was not aware of the extension pack, when you installed guest additions the first time.

---

