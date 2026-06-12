---
title: "Bandwidth Accounting of Bridged VMware VMs"
date: 2008-06-09
forum: Virtualisation
---

### Post by YorYor on 2008-06-09
Is it possible?
Far as I could understand, all bridged connections are handled by vmnet0 (or whichever is defined as the bridge network).

- vnstat can only see vmnet0, it can't filter the individual VMs' traffic
- I've tried iptables forwarding but it doesn't seem to work

Anyone with a solution please?

---

### Post by YorYor on 2008-06-09
One stop-gap solution I just found is darkstat.
However, it can only account for traffic totals, not sure why it's not tabulating the ports and protocols.
All traffic seems to be encapsulated under protocol 6, which is Transmission Control... I'm guessing this is a result of having bridged interfaces? These TC packets are then handled by vmnet0?

---

