---
title: "--cmd-owner option in iptables"
date: 2011-04-26
forum: Security
---

### Post by Borneq on 2011-04-26
The --cmd-owner option was removed in kernel 2.6.14 because was broken with SMP.
Is any way to filtering by process name?

---

### Post by bodhi.zazen on 2011-04-26
> **Borneq said:**
> The --cmd-owner option was removed in kernel 2.6.14 because was broken with SMP.
Is any way to filtering by process name?

Not by process name, only by owner (user or group). Normally these options work best on in the OUTPUT chain.

---

