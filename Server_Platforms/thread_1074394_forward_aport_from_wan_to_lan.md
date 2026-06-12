---
title: "forward aport from wan to lan"
date: 2009-02-19
forum: Server Platforms
---

### Post by genset on 2009-02-19
hi guys

i what to forward a port from the wan to my lan

my setup is

Network interface eth0 connected to the LAN
- Network interface ppp0 connected to the WAN
- eth1's IP is 41.*.*.*
- eth0's IP is 172.16.29.10
- Squid listening on port 3128.
- LAN pc's gateway are set to the Ubuntu server's eth0 IP

i want to forward  port 5900 to pc 172.16.29.5:5900 on lan

please help

---

### Post by linux_tech on 2009-02-19
this explains it

[http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server)

---

### Post by genset on 2009-02-19
ok so i tried that but its still not working :(
sould i use eth1 or ppp0, i connect to the internet with a ppp0 connection but it runs on eth1

---

