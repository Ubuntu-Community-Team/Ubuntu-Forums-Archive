---
title: "ubuntu router no internet connection"
date: 2010-04-12
forum: Server Platforms
---

### Post by pavel989 on 2010-04-12
hey all.

so here was my order of failure: 

i installed a a dhcp server and got it to work.
i began messing with iptables and such to try to forward my internet to dhcp clients. it didnt't work.

i installed webmin hoping that itd fix it. and it didnt.

so now heres what im stuck with. my ubuntu webmin box is behind a router. and this box has an internet connection. i eventually want it to be my gateway and only router on my network, ima make everything else a switch.

clients can connect to the webmin box and get an ip addr. but cannot get on the internet. 

im pretty sure i set up iptables right and i set to forward ip4 in sysctl. BUT i think that amongst all the other crap i was doing i mustve bricked the internet. now idk what to do.

can anyone give me at lest any ideas as to where to begin to debug this

---

### Post by fang0654 on 2010-04-12
Do you have dhcp sending your linux box as the gateway?  Check the routing table on the clients, and see if they have a default gateway going to the linux box.

---

### Post by pavel989 on 2010-04-12
im pretty positive that they use the dhcp server if the gateway, if not the router above that. but im pretty sure i set it to the server cause settign it to the router above didnt work.

---

### Post by dalitso on 2010-04-12
I have always used webmin to get an ubuntu gateway to work.

---

### Post by Iowan on 2010-04-12
Does the server access (ping?) the Internet?

---

### Post by pavel989 on 2010-04-12
ping and w3m worked fine

---

### Post by dalitso on 2010-04-13
Seems like you need to set IP Masquerading/IP forwarding. here's a link that explains how to do it using IP tables (scroll down the page to iptables Masquerading) [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

For me if I want to use IP Tables (linux firewall) I just use the below from that link 
```
sudo nano /etc/sysctl.conf
```
uncomment the following line 
```
net.ipv4.ip_forward=1

```
```
sudo sysctl -p

```

Then I use webmin to set the default gateway in Network configuration, then setup the linux firewall.
I am comfortable using shorewall more than Linux firewall. Its quite easy to do masquerading with shorewall.

---

### Post by pavel989 on 2010-04-13
> **dalitso said:**
> Seems like you need to set IP Masquerading/IP forwarding. here's a link that explains how to do it using IP tables (scroll down the page to iptables Masquerading) [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

For me if I want to use IP Tables (linux firewall) I just use the below from that link 
```
sudo nano /etc/sysctl.conf
```
uncomment the following line 
```
net.ipv4.ip_forward=1

```
```
sudo sysctl -p

```

Then I use webmin to set the default gateway in Network configuration, then setup the linux firewall.
I am comfortable using shorewall more than Linux firewall. Its quite easy to do masquerading with shorewall.


```
pavel@ubuntu-server:~$ sudo sysctl -p
[sudo] password for pavel: 
net.ipv4.ip_forward = 1
net.ipv6.conf.all.forwarding = 1
net.ipv4.conf.default.forwarding = 1
net.ipv4.conf.all.forwarding = 1
pavel@ubuntu-server:~$ 

```

---

### Post by pavel989 on 2010-04-13
wrong format

---

### Post by dalitso on 2010-04-13
Is the gateway working now?

---

### Post by dalitso on 2010-04-13
I tested my server and it is not working by only setting IP masquerade/forwarding. It works when gateway is set in "Network configuration" > routing and gateway" put the IP address of your ADSL router on "gateway" and select it, then save and apply configuration.

I have attached a webmin shot for the setting

---

### Post by pavel989 on 2010-04-13
still a no go.

i think i forgot to mention, i have an ethernet bridge setup for a vpn server (if that changes anything) and i also plan to make this my gateway. i want this to function like a router.

should i just start over?

---

### Post by dalitso on 2010-04-14
I am not sure on that one. Can you post your dhcpd.conf and network interfaces configuration?

```
sudo nano /etc/dhcp3/dhcpd.conf
```

```
sudo nano /etc/network/interfaces
```

---

### Post by pavel989 on 2010-04-14
```
pavel@ubuntu-server:~$ sudo cat /etc/dhcp3/dhcpd.conf
[sudo] password for pavel: 
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "****";
option domain-name-servers 192.168.5.1;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.5.255;
option routers 192.168.5.1;
default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;


log-facility local7;
# DHCP server to understand the network topology.

subnet 10.152.187.0 netmask 255.255.255.0 {
}

# This is a very basic subnet declaration.

# LOCALLAN
subnet 192.168.5.0 netmask 255.255.255.0 {
	authoritative;
	option domain-name-servers 192.168.5.1;
	option broadcast-address 192.168.5.255;
	option subnet-mask 255.255.255.0;
	option routers 192.168.5.1;
	range 192.168.5.100 192.168.5.150;
	}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}


```

```

pavel@ubuntu-server:~$ sudo cat /etc/network/interfaces
auto lo br0 eth0 eth1
iface lo inet loopback

#mapping hotplug
#        script grep
#        map eth0
 
iface br0 inet dhcp
	bridge_ports eth0
	gateway 192.168.2.1

iface eth0 inet manual
	up ifconfig $IFACE 0.0.0.0 up
	up ip link set $IFACE promisc on
	down ip link set $IFACE promisc off
	down ifconfig $IFACE down 
	post-up iptables-restore < /etc/iptables.up.rules

iface eth1 inet static
	address 192.168.5.1
	netmask 255.255.255.0
	broadcast 192.168.5.255
	network 192.168.5.0

```

---

### Post by dalitso on 2010-04-14
It has to be the bridge. Mine has only 2 interfaces, eth0 that connects to the ADSL router and eth1 to LAN. Both interfaces have static IPs and it works as a gateway with the configuration that I posted.

---

### Post by pavel989 on 2010-04-14
thats what i figured. so how do i set my gateway to br0? i figured that this would be the problem but i didnt know where to go from there.
do i edit my /etc/hosts? i really dunno

---

### Post by pavel989 on 2010-04-20
i dont think it was the bridge. i edited some bridge settings and it got me no where.
 

i still cannot figure out why my dhcp clients cannot connect to the internet

---

### Post by epi 1:10,000 on 2010-05-20
I have the same problem.  I can ping the address of the nic card on my ubuntu router's lan side but nothing else.

---

### Post by pavel989 on 2010-05-23
do u have a router outside of ur gateway

---

