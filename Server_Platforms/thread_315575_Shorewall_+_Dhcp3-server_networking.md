---
title: "Shorewall + Dhcp3-server networking"
date: 2006-12-09
forum: Server Platforms
---

### Post by pkelkar on 2006-12-09
Hi,

I have installed ubuntu + dhcp3-server + shorewall with 2 nic. I have connected one nic to dsl modem. other nic is connected to gigabit switch which connects other pcs.

I am unable to browse internet from the client pcs (xp). I checked the ipconfig on xp. ipaddress/gateway/subnet looks okay to me. skype works on xp. 

On linux box, in shorewall config if i specify eth0 as interfaces i cannot to internet. If I change eth0 to ppp0 the ubuntu box is able to connect to internet. 

Are there any settings on shorewall or xp so that it can connect to internet. My shorewall settings are as follows.

interfaces
=======
 
net            eth0          detect          dhcp,routefilter,tcpflags
loc             eth1          detect 
 
Zones
=====
fw             firewall
net            ipv4
loc            ipv4
 
Policy
====
loc        net          ACCEPT
$FW     net          ACCEPT
net        all           DROP            info
all          all           REJECT        info
 
Rules
====
DNS/ACCEPT      $FW           net
SHH/ACCEPT      loc               $FW
ping/ACCEPT       loc               $FW
ping/REJECT       net               $FW
ACCEPT               $FW            loc         icmp
ACCEPT              $FW             net         icmp
]

---

### Post by drokmed on 2006-12-14
Try opening up your policies, then slowly tightening them back down.  Here's a fairly open configuration that works.

Interfaces:

eth0 	net 	Automatic 	dhcp,tcpflags,routefilter,nosmurfs,logmartians 		
eth1 	loc 	Automatic 	tcpflags,detectnets,nosmurfs

Policies:

	loc 	net 	ACCEPT 	None 	None 		
	loc 	Firewall 	ACCEPT 	None 	None 		
	loc 	Any 	ACCEPT 	info 	None 		
	Firewall 	net 	ACCEPT 	None 	None 		
	Firewall 	loc 	ACCEPT 	None 	None 		
	Firewall 	Any 	ACCEPT 	info 	None 		
	net 	Firewall 	ACCEPT 	info 	None 		
	net 	loc 	ACCEPT 	info 	None 		
	net 	Any 	ACCEPT 	info 	None 		
	Any 	Any 	REJECT 	info 	None

Rules:

DNS/ACCEPT	$FW		net
SSH/ACCEPT	loc		$FW
Ping/ACCEPT	loc		$FW
SSH/ACCEPT	net		$FW
HTTP/ACCEPT	net	$FW
Webmin/ACCEPT	net	fw
Ping/DROP	net	$FW
ACCEPT		$FW		loc		icmp
ACCEPT		$FW		net		icmp

---

