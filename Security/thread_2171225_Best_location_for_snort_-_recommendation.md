---
title: "Best location for snort - recommendation"
date: 2013-08-29
forum: Security
---

### Post by rollyah on 2013-08-29
I'm installing ubuntu with the following services:
shorewall
dnsmasq
squid3 (transparent proxy)

this box will serve as a firewall for a network of 30 users with two ISP links and one LAN interface.

Lan is directly connected to a core switch.

What is the best location for snort? i'm thinking of installing it on the firewall itself as all traffic already goes through it.

Any recommendation would be appreciated.

---

### Post by unspawn on 2013-09-01
> **rollyah said:**
> What is the best location for snort? i'm thinking of installing it on the firewall itself as all traffic already goes through it.
 Running a sensor connected directly to the core switch (SPAN port or equivalent), or on the firewall if the first is not an option, should enable Snort to see all traffic passing through. Depending on the amount of traffic seen and logging required you may want to send data to a separate system for storage / processing.

---

