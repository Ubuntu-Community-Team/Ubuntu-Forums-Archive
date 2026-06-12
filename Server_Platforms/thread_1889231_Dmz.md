---
title: "Dmz"
date: 2011-12-01
forum: Server Platforms
---

### Post by shopgeek on 2011-12-01
Greets,

Originally posted in the network and wireless forum, but after some thought, Server Platforms seem more appropriate.  Sorry for the xpost.

I've been using 10.04 as a router/dhcp/dns/proxy/vpn for my small business network. Just awesome. I preroute all port 80 traffic through squid.

We've installed some CRM software recently, and I need to DMZ a machine that is hosting a web service, but I have been having no luck.

Reviewing my current setup, what would be the best way of placing a machine located @ 172.16.2.33 "outside" the router? 

Thanks for any help you can give me.


sg.

Here is my setup:

--- rc.local ---

/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE

--- interfaces ---
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask 255.255.255.252
gateway xxx.xxx.xxx.xxx

# Bridged interface / VPN
auto br0
iface br0 inet static
address 172.16.2.1
netmask 255.255.255.0
broadcast 172.16.2.255
bridge_ports eth1
post-up /etc/init.d/dhcp3-server start
post-up /etc/init.d/openvpn start
post-up /etc/iptables-rules/squid-prerouting.sh
pre-down /etc/init.d/dhcp3-server stop
pre-down /etc/init.d/openvpn stop

auto eth1
iface eth1 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down


--- squid-prerouting ---

iptables -t nat -A PREROUTING -i br0 -p tcp -m tcp --dport 80 -j DNAT --to-destination 172.16.2.1:3128
iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128

---

### Post by Dangertux on 2011-12-01
If you want a TRUE DMZ you're going to need a third interface, however you could just  FORWARD the ports you want to the server in question, though it would not be outside of your network.

---

### Post by shopgeek on 2011-12-01
The system does have a third interface available, currently deactivated.  Once the third interface is enabled, assuming an assignment of eth2, how would you configure the interface to place the target server into a DMZ?

Thanks for your help.

---

### Post by CryptAck on 2011-12-01
Since you have an IP to assign the DMZ, I think you are required to have a third NIC (I'm assuming the DMZ IP is for a different network).

You could try maybe aliasing your eth1, but I don't know how secure that would be...

---

### Post by CryptAck on 2011-12-01
oops, missed your reply.

In that case, you may want to take a look at this [information](http://www.aboutdebian.com/firewall.htm). A bit dated, but I believe the iptable commands still work. :)

---

### Post by shopgeek on 2011-12-01
> **Dangertux said:**
>  however you could just  FORWARD the ports you want to the server in question, though it would not be outside of your network.

As I work with the third nic on the backup router, what would be the best way to forward port 80 from eth0 (WAN) to the webserver located on 172.16.2.33?  Does the prerouting through the squid proxy affect this?

Thanks for you help,

---

