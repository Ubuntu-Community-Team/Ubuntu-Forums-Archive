---
title: "iptables NAT help"
date: 2010-11-30
forum: Server Platforms
---

### Post by jfmanamtr on 2010-11-30
I am having a little trouble setting up a NAT firewall using iptables. I have 1 PC dedicated to being the firewall running Ubuntu 10.04 LTS. There are 2 NICs in this PC. One NIC is connected to the modem & the other is hooked into my router, sharing the connection through to the other PC on my LAN. Thing is that I am having troubles setting this up using iptables. I have it sharing the connection, but can't seem to make it forward 2 ports through to my webserver on the LAN. I am also wanting to setup init.d to control iptables. I have been trying to google this, but haven't found anything useful to get this accomplished. I put the following into rc.local to make the forwarding work:

/sbin/iptables -F
/sbin/iptables -N block
/sbin/iptables -A block -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A block -m state --state NEW -i ! eth0 -j ACCEPT
/sbin/iptables -A block -j LOG
/sbin/iptables -A block -j DROP
/sbin/iptables -A INPUT -j block
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE

Any help to make this work would be greatly appreciated. Thanks for the help in adviance!

~JFM

---

### Post by jfmanamtr on 2010-12-01
*bump*

Any ideas?

---

