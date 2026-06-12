---
title: "3c59x Problem"
date: 2005-11-12
forum: Server Platforms
---

### Post by ScatterBrain on 2005-11-12
I've got a Dell Precision 420 Workstation that I've decided to use for my "do-it-all" server.  Everything is working fine _except_ for the Network Card.  This machine has an integrated 3COM 10/100 nic that is supported by the 3c59x module of the kernel.

The card is detected, the module is properly loaded, but it keeps bringing the link up and down.  In fact if I don't force the card to 10 BaseT Full-Duplex, the NIC is basically useless.

Has anyone else experienced this?  Is there a way that I can force this card to 100 BaseTx Full Duplex (which my switch supports)?

---

### Post by Remmelas on 2005-11-13
[QUOTE=ScatterBrain]
The card is detected, the module is properly loaded, but it keeps bringing the link up and down.  In fact if I don't force the card to 10 BaseT Full-Duplex, the NIC is basically useless.
[/QUOTE]

This sounds similar to a problem we had in an office i used to work at where the pc's were networked with cat3 cable.  We had to run in 10baseT to maintain connectivity and stability on the card.  That said, i'd maybe check your cabling, but have no other useful advice to offer.

---

### Post by joshuapurcell on 2005-12-15
Your switch could be causing the problems. We have Cisco Catalyst switches in our office that refuse to allow the ports to autonegotiate to full duplex even though the ports are capable of running at that speed. The only thing that works for us is to force full duplex:> sudo ethtool -s eth0 autoneg off duplex fullThe cause may not be the card, but installing another card would answer that question.

---

