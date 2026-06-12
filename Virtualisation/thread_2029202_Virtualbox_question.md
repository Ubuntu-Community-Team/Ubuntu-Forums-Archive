---
title: "Virtualbox question"
date: 2012-07-19
forum: Virtualisation
---

### Post by editheraven on 2012-07-19
Does virtualbox  access motherboard northbridge and cpu directly? I mean, if I install the cpu and chipset drivers virtualbox will run faster. I know gpu is just emulated, but cpu?

---

### Post by CharlesA on 2012-07-19
It is uses virtualized hardware. The Guest will see the CPU of the host, but I don't think it will take chipset drivers and whatnot.

---

