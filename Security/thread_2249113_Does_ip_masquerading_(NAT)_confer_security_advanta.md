---
title: "Does ip masquerading (NAT) confer security advantages?"
date: 2014-10-19
forum: Security
---

### Post by haplorrhine on 2014-10-19
Well does it?  It's implemented through firewall settings so naturally I think of security, but I don't see any security-related advantages.

---

### Post by ian-weisser on 2014-10-19
IP masquerading is intended to let multiple machines share a single IP address. Rather like a router does.
It's not a security feature.
It involves rerouting and renaming packets, which is done by iptables (the firewall). So it's often lumped in with other firewall features, and mistaken for a form of security.

See [http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/ipmasq-background2.1.html](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/ipmasq-background2.1.html)

---

### Post by haplorrhine on 2014-10-19
Thank you, ian.  The lack of relevant search results was suggestive, but I needed confirmation.

---

### Post by HermanAB on 2014-10-20
NAT does a little bit of obfuscation that may confuzzle some script kiddies running Windows, but it doesn't do anything against real adversaries.

If you want to explore a network, use ettercap.  You'll be amazed how easy it is:  [http://www.aeronetworks.ca/2013/09/arp-mystery-protocol-that-makes-lan-work.html](http://www.aeronetworks.ca/2013/09/arp-mystery-protocol-that-makes-lan-work.html)

---

