---
title: "no network on M600 server until networking is restarted"
date: 2010-02-05
forum: Server Platforms
---

### Post by thefish on 2010-02-05
Hello

I have an inherited install of ubuntu server 8.0.4.4 on a dell M600 blade. It boots fine, but the network is unresponsive until /etc/init.d/networking restart is run from the console. Has anyone experienced similar issues, or have any tips?

Its a Broadcom NetExtreme II BCM5708S nic

straight after boot, ethtool reports duplex half, and speed as unknown (0) (though link detected is yes)

after networking restart, ethtool shows it as connected at full duplex, 1000M, with no obvious errors. 

eth0 has a static ip configured in interfaces, trying dhcp - dhclient will not sucessfully obtain an ip unless networking is first restarted.

---

