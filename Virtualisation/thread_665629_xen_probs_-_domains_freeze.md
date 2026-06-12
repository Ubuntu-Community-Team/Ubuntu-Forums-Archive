---
title: "xen probs - domains freeze"
date: 2008-01-12
forum: Virtualisation
---

### Post by ludder on 2008-01-12
wanted to play around with xen on ubuntu feisty. 
got some probs with hyperthreading under xm-create-image so i turned it off. 

now the problem is, when i boot up a domain it freezes around:
[ 1374.047143] Failure registering capabilities with primary security module.
[ 1374.133980] thermal: Unknown symbol acpi_processor_set_thermal_limit
[ 1375.134630] kjournald starting.  Commit interval 5 seconds
[ 1375.134956] EXT3-fs: mounted filesystem with ordered data mode.

And there it just stops. Ive tried making both debian and ubuntu domains but they both freeze at the same spot.

Any tricks what could be wrong with my setup?

P4 3,4ghz (no hardware virtualization supported) 1gig ram.

---

