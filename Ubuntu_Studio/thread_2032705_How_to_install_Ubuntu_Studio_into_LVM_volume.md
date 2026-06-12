---
title: "How to install Ubuntu Studio into LVM volume?"
date: 2012-07-24
forum: Ubuntu Studio
---

### Post by jack_spratt on 2012-07-24
Title says it all. The GUI installer apparently doesn't recognise LVM setups. Is there an alternate install CD for Ubuntu Studio that I can use? Or a command line installer instead of the GUI on the standard install disc?

---

### Post by jack_spratt on 2012-07-28
bump

---

### Post by oneillkza on 2013-03-03
I'm way late to this, but for posterity the solution is to install lvm2 via synaptic before running the installer. Then when you choose "do something else", it will show up your LVM partitions / allow you to create new LVM partitions.

---

