---
title: "Ubuntu Server, no internet to wired lan."
date: 2012-02-20
forum: Server Platforms
---

### Post by bigsteve234 on 2012-02-20
Hi all, I have been bashing my head on trying to get internet from my ubuntu server to my wired w7 Pc, 
The Ubuntu server is connect to wired Lan provider with PPPoe Conection, from my server machine I can ping websites and has internet browsing using http tunnel in webmin,
W7 machine connects but says no internet available.
I installed PFsense just to check if its a hardware issue and had internet working in my w7 machine. 

My config for dhcp.
-------------------------------
ddns-update-style none;
authorative;
log-facility local7;

# A slightly different configuration for an internal subnet.
subnet 192.168.1.0 netmask 255.255.255.0 {
	option domain-name-servers 192.168.1.2;
	option broadcast-address 192.168.1.255;
	option routers 192.168.1.2;
	max-lease-time 72000;
	default-lease-time 6000;
	range 192.168.1.100 192.168.1.200;
	}
----------------------------------
My config for Network as you can see, I have 3 nics, and one is wan.


auto lo
iface lo inet loopback

auto br0
iface br0 inet static
       address 192.168.1.2
       network 192.168.1.0
       netmask 255.255.255.0
       broadcast 192.168.1.255
       dns-nameservers 192.168.1.2
       bridge-ports eth1 eth2

     
auto eth0
iface eth0 inet manual
	pre-up /sbin/ip link set dev eth0 up # line maintained by pppoeconf
	post-up iptables-restore < /etc/iptables.up.rules

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider
-----------------------------------------------------
and I have uncommented
net.ipv4.ip_forward=1
----------------------------------------------------

Any help will be muchly appreciated
:popcorn:

---

### Post by oldos2er on 2012-02-20
Moved to Server Platforms.

---

### Post by bigsteve234 on 2012-02-21
My answer was the iptables and bang it worked instantly


ip addr add 192.168.1.0/24 dev eth0
iptables -A FORWARD -o eth0 -i br0 -s 192.168.1.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE

iptables-save | sudo tee /etc/iptables.sav

---

### Post by Iowan on 2012-02-21
> **bigsteve234 said:**
> My answer was the iptables and [COLOR="Red"]bang[/COLOR] it worked instantly
Head bang? ](*,)

[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

