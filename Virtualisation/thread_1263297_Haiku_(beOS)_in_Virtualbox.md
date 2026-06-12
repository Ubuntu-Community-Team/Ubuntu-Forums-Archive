---
title: "Haiku (beOS) in Virtualbox"
date: 2009-09-10
forum: Virtualisation
---

### Post by Mateo on 2009-09-10
I had VMWare Workstation installed (a "borrowed" copy) and Haiku worked fine.  When I switched to Virtualbox, the network no longer works.  I tried NAT, bridged, host-only.  None of them work.  I don't know what to do. Advice?

---

### Post by Zhwazi on 2009-09-11
Have you tried setting the emulated NIC to something else? It may be that the interface VMware gave you by default has a driver in Haiku but the one that Virtualbox provides by default does not. I know this to be the case with Windows 2003 Server and Windows XP.

Edit: Found out one that works, use the Intel Pro/1000 T. This works on the Haiku image I got in February. I think this is also one that Windows recognizes out of box.

---

