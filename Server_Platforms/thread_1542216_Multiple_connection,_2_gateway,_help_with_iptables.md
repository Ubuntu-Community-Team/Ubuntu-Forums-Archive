---
title: "Multiple connection, 2 gateway, help with iptables needed"
date: 2010-07-30
forum: Server Platforms
---

### Post by Nicolas_VP on 2010-07-30
I have primary internet connection as eth0 (public IP, X1.X1.X1.X1) and secondary for the backup-diagnostic reason eth1 (behind the router 192.168.1.Y). The default gateway is set to eth0. SSH is configured to listen on all interfaces. However, when packets are received from eth1, they are going back to default gateway eth0. How to configure in iptables, that when ubuntu-server receives packet from specific port in should return it to the specific gateway. Thank you very much in advance.

---

