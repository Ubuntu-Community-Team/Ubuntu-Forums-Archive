---
title: "Call to WMI Interface crashes XP app"
date: 2008-12-22
forum: Virtualisation
---

### Post by notessensei on 2008-12-22
I recently upgraded to 8.10. I have VMWare Workstation 6.5 and Virtual Box 2.1. I have a XP guest with a Windows (Java) application that calls the WMI interface to determine virtualization and network status.
After upgrading to 8.10 this application crashes in both VMWare and VirtualBox. If I remove the virtual network cards (disabling is not enough), the application runs without fail. But no ntwork, no fun.
Seems like the changes in the network interface of 8.10 require special attention? My machine is a T61 (tried both: with/without hardware support for virtualization).
Any hints?
:-( stw

---

### Post by notessensei on 2008-12-22
Turned out Virtualization is innocent: The application required the "DCOM Server Process Launcher" service which I had deactivated on the quest towards a lean mean guest OS.

---

