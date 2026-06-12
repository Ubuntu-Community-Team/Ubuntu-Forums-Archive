---
title: "Compaq DL360 G1"
date: 2010-02-28
forum: Server Platforms
---

### Post by iissmart on 2010-02-28
This question isn't really Ubuntu-specific, it's more of a hardware question. I just received a Compaq DL360 (Generation 1) 1U server ([specs](http://h18000.www1.hp.com/products/quickspecs/10530_na/10530_na.HTML)), and I was wondering if this would work well as a gigabit router. It currently has two Pentium III CPU's at 1.00 Ghz each and 512MB of ram (one stick). It comes with two 10/100Mbps ports on the motherboard, but it also has a gigabit NIC in the PCI slot. I was thinking of just getting an Intel Pro/1000 dual-port NIC (PCI-X) and putting it in the free PCI-X slot and using that for inbound and outbound traffic (and leave the other ethernet ports unused).

So I really have two questions:
1) Are two PIII CPU's at 1Ghz each enough for gigabit routing speeds? My internet speed is only 10Mbps/1Mbps so NAT traversal wouldn't be nearly that quick.

2) Will a dual-port PCI-X NIC be fast enough for gigabit speeds, since they are on the same bus/card? I really wish this server came with two separate PCI-X ports, then I would use two separate PCI-X single-port NICs.

The reason I don't want to use the current Gbit NIC is because I heard Intel Pro series cards work the best (least CPU interrupts), but they apparently only make these on PCI-X or PCI-E, not plain PCI.

Any suggestions?

---

