---
title: "Ubuntu Server 11.10 + Squid3 +Dhcp3"
date: 2012-04-04
forum: Server Platforms
---

### Post by swat565 on 2012-04-04
Hello all, needless to say I'm having trouble with a project of mine. Still new to Ubuntu and Squid, but giving it a shot. Trying to set it up as a Transparent Proxy, and to also act as a DHCP server. Been following this guide:
[URL="http://www.ubuntugeek.com/setting-up-ubuntu-10-04-lucid-server-with-squid-3-as-a-transparent-proxy.html"]http://www.ubuntugeek.com/setting-up-ubuntu-10-04-lucid-server-with-squid-3-as-a-transparent-proxy.html
[/URL]
 
**My network**:
*[LAN]*---192.168.2.0/24 network---*[Ubuntu Server]*---192.168.1.0/24---*[PIX 501]*-->*[WAN]
 
**-I can ping on the Ubuntu interface on the PIX side via 192.168.1.250 successfully**
 
**-Unable to get an address from the 192.168.2.0 network from Ubuntu Server**
**-Unable to set statically an address on 192.168.2.0 network and get any communication**
**-Shows network resources not loading on boot:**
```
Waiting for network configuration...
Waiting 60 more seconds for network configuration...
```
 
**Setup:**
Ubuntu 11.10 x86 install
Squid3
Dhcp3
 
**Configs:**
 
/etc/network/interfaces
```
auto eth0
iface eth0 inet static
address 192.168.1.250
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.88
 
post-up iptables-restore < /etc/iptables.up.rules
 
auto eth1
iface eth1 inet static
address 192.168.2.1
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
```
 
/etc/squid3/squid.conf
```
http_port 3128 transparent
acl our_networks src 192.168.2.0/24
acl localnet src 127.0.0.1/255.255.255.255
http_access allow our_networks
http_access allow localnet
cache_dir ufs /var/spool/squid3 18000 16 256
```
 
Created iptables /etc/iptables.up.rules
 
```
*nat
 
-A PREROUTING –i eth1 –p tcp –m tcp –dport 80 –j DNAT –to-destination 192.168.2.1:3128
-A PREROUTING –i eth1 –p tcp –m tcp –dport 80 –j REDIRECT –to-ports 3128
-A POSTROUTING –s 192.168.2.0/24 –o eth0 –j MASQUERADE
 
*filter
 
-A INPUT –i lo –j ACCEPT
-A INPUT –m state –i eth0 –state REALATED,ESTABLISHED –j ACCEPT
-A INPUT eth1 –j ACCEPT
-A INPUT –p tcp –m tcp –dport 22 –j ACCEPT 
-A INPUT –j LOG
-A INPUT –j DROP
-A FORWARD –i eth1 –j ACCEPT
-A OUTPUT –o lo –j ACCEPT
-A OUTPUT –o eth1 –j ACCEPT
-A FOWARD –o eth1 –j ACCEPT
-A FORWARD –s 192.168.2.0/24 –o eth0 –j ACCEPT
-A FORWARD –d 192.168.2.0/24 –m state –state ESTABLISHED,REALTED –I eth0 –j ACCEPT
```
 
/etc/default/isc-dhcp-server
 
```
INTERFACES="eth1"
option netbios-name-servers 192.168.2.1
```
 
/etc/dhcp/dhcpd.conf
```
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.2.255;
option routers 192.168.2.254;
option domain-name-servers 192.168.2.1, 192.168.2.2;
option domain-name "mydomain.example";
 
subnet 192.168.2.0 netmask 255.255.255.0 {
range 192.168.2.10 192.168.2.100;
range 192.168.2.150 192.168.2.200;
```

---

