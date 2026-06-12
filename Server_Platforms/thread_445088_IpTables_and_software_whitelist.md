---
title: "IpTables and software whitelist"
date: 2007-05-15
forum: Server Platforms
---

### Post by franz1789 on 2007-05-15
Is it possible to make a rule, and allow all the connection (inbound and outbound, for all the port) of a program? I need it for aMule, because I tried to open its ports, but it doesn't find any source or client...
Thank you!!!:)

---

### Post by dmizer on 2007-05-16
might try the help files for the software configuration first ... that's where i found this:
[http://www.amule.org/wiki/index.php/Firewall](http://www.amule.org/wiki/index.php/Firewall)  the redhat instructions should be similar if not identical.

alternatively, you could install a gui like firestarter for configuring your iptables.

---

### Post by Vola on 2007-05-16
I don't know if you have a firewall problem here, maybe you need to configure amule first

Anyway you can flush the iptables chains with

sudo iptables -F

note if you have a router for internet connection maybe this has a firewall inside.

---

