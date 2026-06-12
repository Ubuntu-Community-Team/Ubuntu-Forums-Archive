---
title: "LXDE/Openbox Working Again in Raring"
date: 2013-03-16
forum: Ubuntu Development Version
---

### Post by VinDSL on 2013-03-16
Just did a daily upgrade, via Synaptic, and noticed LXDE was in the mix.

I quit using LXDE/Openbox a couple of months ago, because 'lxsession' was using 100% CPU, sitting idle at the desktop.

If I wished to use LXDE/Openbox, I had to login, disable 'lxsession', then re-enable it later, so I could logout/restart/shutdown et cetera.

Anyway, after today's LXDE upgrade, everything is back to normal!  :)

---

### Post by Sworddragon on 2013-03-17
LXDE was working fine for me all the time in the most parts. Only LXDM is making some troubles. It has a bug which forces lxdm-binary to use 100% cpu time of one core if the home directory is encrypted with ecryptfs. But currently I'm even not able to login anymore with LXDM due to another bug.

---

