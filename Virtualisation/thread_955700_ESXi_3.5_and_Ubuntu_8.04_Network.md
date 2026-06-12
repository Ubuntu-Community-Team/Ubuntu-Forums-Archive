---
title: "ESXi 3.5 and Ubuntu 8.04 Network"
date: 2008-10-22
forum: Virtualisation
---

### Post by RayRuest on 2008-10-22
I have recently set up ESXi and attempting to get Ubuntu running.  I have converted a VM to ESX, as well as start one from scratch.  Both Ubuntu setups work fine, except for the networking.  I cannot seem to get networking to function properly.  I know ESXi is working fine because I can use other VMs fine.  Any ideas?  I've got a feeling it's a driver/interface thing...  but I'm not experienced with Linux enough to diagnose myself.  Any ideas?

---

### Post by RayRuest on 2008-10-23
Found the problem... turns out it wasn't Ubuntu after all.  I noticed in ESX that the network adapters were not reporting the entire IP range of my network.  After examining the switch, I realized that the ports were configured LACP.  I turn this off at the switch, ESX adjusted after about 60 seconds, and Ubuntu came online immediately!

---

