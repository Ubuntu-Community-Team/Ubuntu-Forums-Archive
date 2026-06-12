---
title: "WINE and Nvidia G105M"
date: 2009-06-15
forum: Wine
---

### Post by Cadeyrn on 2009-06-15
I've been wondering for a while, why do WINE 1.0.1 and WINE 1.1.23 not work with many apps other people can use just fine? Well, after some snooping I realized WINE thinks I have no video card. In reality I'm running a System76 Pangolin Performance, which means I have an Nvidia GeForce G105M installed under custom System76 drivers. WINE doesn't know I have a 512MB video card and is instead making full usage of my <sarcasm>ever capable</sarcasm> 64MB X11 server. How do I fix this?

EDIT: Heh... Really sorry for making 2 pointless topics in one day--I fixed it myself. The Direct3D registry keys are a great way to configure WINE's video card.

---

