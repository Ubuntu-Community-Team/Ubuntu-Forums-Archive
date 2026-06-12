---
title: "Boot Hang if nvidia installed"
date: 2023-03-10
forum: Ubuntu Development Version
---

### Post by crcarson on 2023-03-10
Been having problems with 23.04 since the Dec daily build.  Seems if I install selecting the nvidia-driver-390 the system hangs at first boot.  Can not get the system up to document the failure.  Booted in recovery mode and apt --remove nvidia-driver-390 --purge and then the system will reboot.  Just downloaded the latest daily build (3-10-23) and did an install selecting external graphic drivers and the system went into the same hang on first boot.  Installing with out selecting external graphic drivers and the system installs and runs normally.

Any suggestion on how to document this failure?

---

### Post by osse7 on 2023-03-10
you can grab errors/warnings from "journalctl -b -1 | grep NVIDIA" from a console and without quotes, to see where is/are the conflict(s); then search for related reported bug (if any) on launchpad & git

Gnome-shell is actually partly upgraded and mutter is not yet in the place for recent nvidia version; so try booting with a <390 version to know if that help for the moment

---

### Post by crcarson on 2023-03-10
Will try to document problem through the journalctl as suggested when/if I reinstall.  Currently have a working 23.04 system without nvidia.

---

