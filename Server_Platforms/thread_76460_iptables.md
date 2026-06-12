---
title: "iptables"
date: 2005-10-15
forum: Server Platforms
---

### Post by billiejoex on 2005-10-15
I was wondering why iptables isn't installed by default on ubuntu.

---

### Post by GTvulse on 2005-10-15
iptables, the userland tools to control the kernel firewall, are installed by default.

Do you mean why there is no active firewalling by default? That's because of a different philosophy on security to certain very popular RPM -based distros that install all network services **active** by default, therefore they have to include an active firewall configuration to protect the unsuspecting user; very much the same philosophy as MS operating system products but these Linuces have in their favor that the firewalling was used from the beginning. :-)

A default, vainilla, Ubuntu installation does not have active network services open to the network, therefore there is no need to have active firewalling configured in the kernel. If you install and open services to the network well..., you probably need a firewall.

I 'd suggest shorewall. It is not in the Ubuntu 5.10 installation CD but it is officially supported, that is, it is part of main as seen by the logo icon that shows up in Synaptic and it is included in the Ubuntu Server CD (which is not released yet as far as I know).

---

