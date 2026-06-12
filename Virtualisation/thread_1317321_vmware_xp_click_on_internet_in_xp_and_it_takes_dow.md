---
title: "vmware xp click on internet in xp and it takes down whole network"
date: 2009-11-06
forum: Virtualisation
---

### Post by sdowney717 on 2009-11-06
It just does, the dns server is gone and you cant ping anything.
To fix means you have to unplug the router, reboot the ubuntu host and never click the icon "internet connection is disabled" in network manager.

part of the issue may be i added a physical second nic card. VMware had to be recompiled because the bridge was mapping to a name that no longer existed in the host (eth2 or eth3). somehow my ubuntu os is back on eth0

---

