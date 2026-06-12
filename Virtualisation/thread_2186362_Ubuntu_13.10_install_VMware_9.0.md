---
title: "Ubuntu 13.10 install VMware 9.0"
date: 2013-11-07
forum: Virtualisation
---

### Post by priyaafsar on 2013-11-07
When I install VMware 9.0 on my Ubuntu 13.10, there come to the problem "Before you can run VMware, several modules must be complied and loaded into the running kernel."

And , when I click the INSTALL button, nothing happened.

---

### Post by priyaafsar on 2013-11-07
Can anybody help me?

---

### Post by ubfan1 on 2013-11-08
You can force the compilation with:
sudo vmware-modconfig --console --install-all
but my 13.10 still had some issues with vmnet and one other.  A starting place at least.

---

### Post by ubfan1 on 2013-11-09
My issues with vmplayer 5.02 on Ubuntu 13.10 went away with an upgrade to vmpayer 6.01.  The install resulted in a running player.

---

### Post by cariboo on 2013-11-09
Moved to VIrtualization.

---

