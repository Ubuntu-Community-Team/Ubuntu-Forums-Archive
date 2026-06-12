---
title: "stopping apache2 ... takes too long"
date: 2011-04-29
forum: Server Platforms
---

### Post by Skaperen on 2011-04-29
During a shutdown when there is a network configuration problem (need to reboot to reset it), the init step where it stops apache2 is taking too long.  Apparently apache is needing to do some DNS lookup.  Any way to get this to not happen short of a script to just hunt down and kill all apache processes?

---

