---
title: "Ethernet Bonding Dosen't Work in Ubuntu 8.04?"
date: 2010-03-17
forum: Server Platforms
---

### Post by kevin11951 on 2010-03-17
After installing Ubuntu 8.04.4, I tried to (for the first time) setup interface bonding.  It doesn't seem to work no matter how many how-to's I follow.

I am trying to setup "mode=0" on a server connected to a switch that does not support port trunking.  But, from what I understand, I can do round-robin w/o a special switch.

---

### Post by kevin11951 on 2010-03-18
Anyone...?

(Bump)

---

### Post by BobVila on 2010-03-18
> **kevin11951 said:**
> Anyone...?

(Bump)

We'll need some more info on what you've tried to give some decent feedback... 

FWIW, mode 4 (802.3ad (LACP)) is the only bonding method I've used that I thought was worth the hassle, but, as you know, it requires a switch that supports link aggregation.

---

### Post by inphektion on 2010-03-18
it def works. post your eth configs. oh and x64 or 32

---

