---
title: "problem with forwarding"
date: 2009-01-04
forum: Server Platforms
---

### Post by davortot on 2009-01-04
Hi,

I'm having problems with forwarding on my ubuntu server. The issue is that the clients can not send/receive any traffic. I have been looking for solution for very long but can&#8217;t see to find it. So please help.
Ubuntu server with 2 nic.
Eth0 external network
Eth1 internal network
**/etc/network/interfaces:**
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet static
address		192.168.1.1
netmask	        255.255.255.0
broadcast	192.168.1.255
network		192.168.1.0

**/etc/default/dhcp3-server:**
INTERFACES="eth1"

**/etc/ dhcp3/dhcpd.conf:**

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.100 192.168.1.130;
  option domain-name-servers 192.168.2.2, 193.162.153.164, 194.239.134.83;
  option domain-name "ftot.dk";
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 7200;
}

**In /etc/init.d/networking** added the line
echo 1 > /proc/sys/net/ipv4/ip_forward

**iptables:**
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


client attached to eth1 obtains ip: 192.168.1.101 and can ping
192.168.1.1 but not anything outside

please help

---

