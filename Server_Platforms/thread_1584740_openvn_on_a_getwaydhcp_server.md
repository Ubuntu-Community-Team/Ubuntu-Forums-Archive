---
title: "openvn on a getway/dhcp server"
date: 2010-09-29
forum: Server Platforms
---

### Post by pavel989 on 2010-09-29
i have a lucid server box running a dhcp server and webmin.

i want to bridge openvpn to the network that the dhcp server serves.

all the configurations ive seen, id essentially have to install openvpn onto a computer underneath the dhcp server to accomplish this.

can anyone help me out?
is this even possible?

---

### Post by sinclair86 on 2010-09-30
[http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html](http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html)

ive followed this tutorial millions of times on multiple servers. if you run into problems let me know

---

### Post by pavel989 on 2010-09-30
i have it bridged. the thing is, that the box is going to be my gateway, so i want to give out ip address on the subnet that the dhcp server is. which i got that working.

however, once i get connected, im on the same subnet is my subnet behind the gateway, but cannot access it.

iptables was configured through webmin to allow all traffic.

---

### Post by sinclair86 on 2010-10-06
are you trying to do this on one ethernet card? what does your setup look like?

```
internet <---> eth0 [ubuntu server] eth1 <----> private network?
```

or

```
internet <---> private network
                        /\
                        ||
                        ||
                 [ubuntu server]
```

---

