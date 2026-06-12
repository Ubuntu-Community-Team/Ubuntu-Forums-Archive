---
title: "HP Proliant ML370 and Dell Poweredge 2300"
date: 2008-10-02
forum: Server Platforms
---

### Post by petatkinson on 2008-10-02
Just been gifted the above and wondered what best use I should put these two beasts to.I understand the spec of them and was just asking your opinion on how best to use them with Ubuntu.They are probably power hungary animals and cost a packet when built but thats technology for ya.Currently running Hardy Heron on standard dual core units but was very interested to see how I can use these machines.

---

### Post by petatkinson on 2008-10-03
Ok.Either everyone is jealous,possibly,no one has a clue,doubtful or no one cares,probably.Just thought i'd ask to see if anyone could share their opinion on this.

---

### Post by windependence on 2008-10-04
Well if it was me, I'd run VMware ESXi on them and make them into virtual data centers. You could run 5-10 VMs on each box with the right amount of RAM in them. ESXi is free, and it doesn't need a host OS like Vmware Server so it is wayyy more efficient.

You could also make them into firewall/mail filter appliances with something like pfsense or Untangle.

-Tim

---

### Post by petatkinson on 2008-10-05
Thanks for the advice.Going to collect them tomorrow.I will fire them up and see what happens.Think they were used as W2003 servers but I'd rather put DR Dos on them or use them as garden furniture than use that c**p.

---

