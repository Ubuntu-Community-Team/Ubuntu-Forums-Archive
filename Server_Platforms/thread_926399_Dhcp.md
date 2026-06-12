---
title: "Dhcp"
date: 2008-09-21
forum: Server Platforms
---

### Post by NightShade01 on 2008-09-21
Hello all quick question. I was looking over the documentation and I see this sample config file:

# Sample /etc/dhcpd.conf
# (add your comments here) 
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.1, 192.168.1.2;
option domain-name "mydomain.example";

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.100;
range 192.168.1.150 192.168.1.200;
} 

To my understanding the clients will get an address either in the 1.10-1.100 range or 1.150-1.200 range.  Is this similar to creating scopes of IP addresses on a windows 2003 box?

---

### Post by RealPSL on 2008-09-22
Yes the range directive represents the scope.

---

