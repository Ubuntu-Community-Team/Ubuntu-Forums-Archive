---
title: "Swap eth0 and eth1 around!"
date: 2006-10-02
forum: Server Platforms
---

### Post by paul.maddox on 2006-10-02
Hi All,

Strange problem with one of our PowerEdge servers...

It has a dual nic adapter (broadcom) which Ubuntu seems to have picked up the wrong way round.

NIC number 1 is eth1
NIC number 2 is eth0


Is there any way to swap these around with ubuntu?

---

### Post by StickyStyle on 2006-10-02
IIRC the ethXX number comes from the order the kernel probes the cards, which in turn comes from the order in there bus id.  So you cant really change it for bulitin cards easily (pci ones you could swap slots).  Perhaps dell put the sticker on backwards ;-)

(checks his server room)

I have PE 350's, 650's, 1650's, 1750's, 1850's, and 2650's and they all have there ports numbered correctly, what model are you having this issue with?

---

### Post by paul.maddox on 2006-10-02
We have lots of dell servers, SC1425's, PE1850's, PE2950's, PE2900's and this one PE1950.

It's only the PE1950 that's causing the problem.
The left eth is labelled 1, the right eth is labelled 2.

I just spent 3 hours this afternoon trying to work out why eth0 couldn't get a DHCP lease even though the kernel had detected the card fine only to find out that when I plug LAN into port 2, eth0  is the corrosponding interface.

It's not a major problem, just annoying!

---

### Post by ethan-p on 2006-10-26
I know that this is an old thread, but I wound up here after a google search and this was very relevant to my issue.

To add to the discussion, the kernel tends to detect nic's as described earlier, but it gets worse when you throw a third card into the equation.

Onboard NIC interface 2=eth0
Add-on PCI NIC=eth1
Onboard NIC interface 1=eth2

---

