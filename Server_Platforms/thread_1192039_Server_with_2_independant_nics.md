---
title: "Server with 2 independant nics"
date: 2009-06-19
forum: Server Platforms
---

### Post by zouriel on 2009-06-19
i want to setup a dhcp server
the config i would like to do is have one nic going to the outside world and the secondary nic handling all of the traffic internal to my network.
I can not find a decent how-to running dual nics... 

can someone point me in the right direction

---

### Post by tgalati4 on 2009-06-19
Add your entries to /etc/network/interfaces

You will probably have eth0 and eth1 as entries.

You may have to reboot for changes to take effect.  You may also have to reboot your routers/dsl modem for them to detect your new addressing scheme.

apropos dhcp

---

### Post by cariboo on 2009-06-19
To make things easier, use a different netblock for the internal network, than the external connection. Set the external nic for dhcp, and the internal nic to a static i address, setting the internal ip address to static allows the other computers on the network to always get their ip address from the same ip address instead of searching for it on every reboot.

---

