---
title: "Closed ports on a paravirtualized system"
date: 2011-07-07
forum: Server Platforms
---

### Post by epoch2038 on 2011-07-07
I have a machine running XenServer that hosts two Ubuntu-based servers, one a hardware-virtualized machine, the other paravirtualized. I'm attempting to install the Zentyal small-business server on both (as an experiment due to my inability to get it working on just the paravirtualized system) and have found that iptables has no effect on the paravirtualized system, through nmap-ing the machine after changes to the connection tables. Apache2 and other services such as the OpenSSH-Server have no problem allowing for connections, but the Zentyal-core package is unable to set a port to receive connections. And on the HVM, there is no problem at all. 

I feel the root of the problem is in someway related to either the kernel or Apache, as I have had issues with apache on another PV system, which results in the inability of ProFTPd to start, yet no issues at all when booting the VM as hardware-virtualized with the exact same kernel. Or perhaps since iptables requires the kernel to be enabled for it, booting with the PV code activated somehow disrupts that mechanism? I don't know. I'm way over my head.

Right now I'm simply trying to find out what might cause iptables to not function properly.

Thank you!

---

