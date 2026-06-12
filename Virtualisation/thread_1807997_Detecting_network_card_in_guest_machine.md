---
title: "Detecting network card in guest machine"
date: 2011-07-19
forum: Virtualisation
---

### Post by josir on 2011-07-19
Hi folks,

I could not reach the network card on one of my guest machine.

Ubuntu 10.04 Host with KVM / libvirt management

2 Guests: 
Ubuntu 9.04 - The first one is working fine.
Ubuntu 8.04 - The second one does not recognize network card.

I issued a lspci and the network card is listed.
But when I try mii-diag ou mii-tool it does not recognize eth0-.

Does somebody have any glue?

Thanks in advance,
Josir Goems

---

