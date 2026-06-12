---
title: "External ARP Poisoning Attacks"
date: 2008-05-21
forum: Security
---

### Post by eniacpx on 2008-05-21
Does anyone know, do the major ISP's make any attempt to stop people from wreaking ARP havoc on their local node? (In the cable internet world, I know nothing of DSL)

I ask because if I run tcpdump on my external interface I see all the ARP traffic for my node, it seems I would be able to easily spoof the gateway addresses and bring down my entire node, or run a man-in-the-middle attack on any of the IP's I see responding to ARP traffic.

With the prevalence of unsecured wireless networks in my area it just seems like we might have more issues with this. :)

---

### Post by turinglabs on 2008-05-22
Most ISP's will have switches with "sticky arp" enabled to prevent ARP spoofing attacks. Any switch ports with sticky arp enabled will not update their cached MAC address in response to an ARP reply.

---

