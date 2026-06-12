---
title: "Real vLANs with NATing (not bridging)"
date: 2010-12-13
forum: Virtualisation
---

### Post by kevpatts on 2010-12-13
I'm looking to create 3 vLANs on my machine and only allow them to communicate on specific ports. This is to replicate a setup using vLANs and a live Firewall routing traffic between them.

I can create the vLANs all right and place the machines on them, but how do I set up the port forwarding rules to send the traffic to the correct virtual box within each vLAN?

---

### Post by HermanAB on 2010-12-14
Howdy,

Port forwarding is tied to IP addresses and Port Numbers, not VLANs.

---

