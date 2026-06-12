---
title: "OpenVPN Setup."
date: 2012-08-31
forum: Server Platforms
---

### Post by sandyd on 2012-08-31
Ive been having a bit of a setup problem with my current VPNs.

I have a VPN that connects me to my parent's house whenever they need help or w/e

I have a VPN that connects me to my server network.

The problems start when both become activated. :(

Some connections go through my parent's side, and others go through my server network side. I just want all network connections to go through the VPN that leads to my server network.

Any idea on where I should start with this?

---

### Post by SeijiSensei on 2012-08-31
Sounds like a routing problem.  Do you set up routes using the "up" directive in openvpn.conf?

Connect to both remotes, then run "route -n" and paste the results here.

---

### Post by sandyd on 2012-08-31
nvm - figured it out.

I was pushing two gateways (push redirect-gateway) to my computer (one from my parent's home, and one from my servers).

Removed the ```
push redirect-gateway
``` line from my parent's home, and I was left with one gateway, which worked fine.

---

