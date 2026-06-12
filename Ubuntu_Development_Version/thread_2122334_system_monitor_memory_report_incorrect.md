---
title: "system monitor memory report incorrect"
date: 2013-03-04
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-03-04
System monitor reports only 993 Mb of 2Gbs.

raring-desktop-amd64.iso

---

### Post by jbicha on 2013-03-04
Please file a bug.

---

### Post by ManamiVixen on 2013-03-04
Are you using onboard graphics? Ubuntu could be reporting the ram it has access to but not all total ram as say a gigabyte is set aside for onboard. If that is the case, chck you video settings in BIOS.

---

### Post by ventrical on 2013-03-05
> **ManamiVixen said:**
> Are you using onboard graphics? Ubuntu could be reporting the ram it has access to but not all total ram as say a gigabyte is set aside for onboard. If that is the case, chck you video settings in BIOS.

PCI express, Nvidia.

btw .. this is on a fresh daily raring64bit install.

---

### Post by ventrical on 2013-03-05
> **jbicha said:**
> Please file a bug.

Against gnome-system-monitor?

so I did that and it's already been reported...

---

### Post by ventrical on 2013-03-05
Easier fix is to just edit the host and hostnames files:

ventrical@ventrical-Mir-WaylandStation:~$

whoops .. wrong forum :)

---

