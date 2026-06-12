---
title: "Can you mix key and password authentication on different interfaces?"
date: 2011-04-14
forum: Security
---

### Post by spynappels on 2011-04-14
Ok, this may be a stupid question, but is it possible to set up the sshd daemon to allow password authentication on one interface, such as tun0 (a VPN interface) while only allowing public key authentication on eth0 (Internet facing interface)? Or is the only way to do this to run 2 different sshd daemons on different ports? I know you can specify the port the service is bound to as well as the interface, but can different authentication settings be set for each interface easily?

---

