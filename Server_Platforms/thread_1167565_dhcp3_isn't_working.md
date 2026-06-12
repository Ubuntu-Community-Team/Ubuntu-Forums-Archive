---
title: "dhcp3 isn't working"
date: 2009-05-23
forum: Server Platforms
---

### Post by dinodom000 on 2009-05-23
I am trying to get a ubuntu server (9.04) to work as a http caching proxy, a dns caching server, and as a dhcp server.

Im running into a problem configuring the dhcp server.

I installed dhcp3-server

and went the the ubuntu server documentation and it still doesn't work.

/etc/dhcp3/dhcpd.conf:

```

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
option domain-name-servers 208.67.222.222, 208.67.220.220;

default-lease-time 86400;
max-lease-time 604800;

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.100 192.168.0.200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
}

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}


```

When i start the dhcp server it wont give the router a connection.

Please let me know i there is anything else i need to show. I fairly good at linux but this just has me stumped.

Thanks in advance for your help!

Network map:

[_DSL Modem_]------[_Ubuntu Server_]-------[_Wireless Router_]-----{Everything else}

---

### Post by koenn on 2009-05-23
your dhcp conf looks OK, unless I'm overlooking a syntax error or so.

> **dinodom000 said:**
> 
Please let me know i there is anything else i need to show.


Your network looks funny, maybe you should explain what you're trying to do and how you configured it so far, especially 

- which IP addresses you've assigned manually so far, and which interfaces you expect to get an address from the DHCP server. 

- it looks like you want the ubuntu server to be an internet gateway for the wireless LAN. Do you have any firewalling going on there ?

---

### Post by mellowd on 2009-05-23
I see where you're going here, but why not use the wireless router as the DHCP server?

---

### Post by koenn on 2009-05-23
> **mellowd said:**
> I see where you're going here, but why not use the wireless router as the DHCP server?
It probably already does that - dhcp doesn't traverse routers (not without some extra work, anyway) so the ubuntu server's dhcp most likely only configures the router interface it is connected to, and the WLAN router's dhcp server configures the WLAN hosts

That's why i said it looks kinda funny and asked for the OP to explain a bit what he has in mind ...

---

### Post by mellowd on 2009-05-23
> **koenn said:**
> It probably already does that - dhcp doesn't traverse routers (not without some extra work, anyway) so the ubuntu server's dhcp most likely only configures the router interface it is connected to, and the WLAN router's dhcp server configures the WLAN hosts

That's why i said it looks kinda funny and asked for the OP to explain a bit what he has in mind ...


Depends. Broadcasts won't be forwarded by a layer3 port, but most home routers have a switch backplane. Therefore as long as both server and clients are on the same plane and subnet they'll communicate just fine (as well as all broadcasts)

I'd just use the wireless router as the DHCP server. If you want to set it up as you want to practice DHCP you can look deeper into the problem.

What wireless router are you using? What subnets are you using for each hop? You can install wireshark on a client and capture dhcp packets to see if you're getting 2 way communication

---

### Post by koenn on 2009-05-23
> **mellowd said:**
> Depends. Broadcasts won't be forwarded by a layer3 port, but most home routers have a switch backplane. Therefore as long as both server and clients are on the same plane and subnet they'll communicate just fine (as well as all broadcasts)

I see what you mean.

When I saw this 

 _]-------[_Wireless Router_]-----{

I assumed a router with 2 interfaces, each one in a different net (possibly with a build-in switch on one side or so). But it is indeed possible that the server is also in the same segment as "all the rest"

---

### Post by dinodom000 on 2009-05-23
I have a Dlink dir-615 router.

So far i have the ubuntu server doing the PPPoe for the DSL modem. I have an onboard Ethernet port (eth0) and an add in one (eth1). The DSL modem goes into eth0 and eth1 connects to the router. 

> I see where you're going here, but why not use the wireless router as the DHCP server? 

I want the server to be able to give the router an ip address (it doesn't matter what it is) and i want the router to then use dhcp to configure all the computers/servers beyond that as if the server wasn't there.

> Your network looks funny, maybe you should explain what you're trying to do and how you configured it so far, especially

- which IP addresses you've assigned manually so far, and which interfaces you expect to get an address from the DHCP server.

- it looks like you want the ubuntu server to be an internet gateway for the wireless LAN. Do you have any firewalling going on there ?

I haven't manually assigned any. And i want the ubuntu server to give an IP to the router. I haven't set up any firewalling yet but that is another function i want it to provide to my internal network later.

I have attached a more detaild network map as a picture i threw together in paint. Hope it helps.

Thanks!

---

### Post by koenn on 2009-05-23
also, apparently both eth1 of the server, and the external interface of the wireless router, have 192.168.0.1 as address.

That can't be right.
 
Also, you said you wanted that address ro be assigned by dhcp, and that dhcp isn't working, so how you got that address ?

---

### Post by dinodom000 on 2009-05-23
Well in the dhcp config settings i have it set as 192.168.0.1 for eth1 (option routers 192.168.0.1), and in the /etc/network/interfaces file i have eth1 set as 192.168.0.1 static.

Being that the servers dhcp ranges from 198.168.0.100-200 i would assume the routers external address would be 198.168.0.100 as it will be the only device. The routers internal address is 192.168.0.1 i have it set as that in the routers config page.

---

### Post by koenn on 2009-05-24
> **dinodom000 said:**
> in /etc/network/interfaces file i have eth1 set as 192.168.0.1 static.

The routers internal address is 192.168.0.1 i have it set as that in the routers config page.
And if a packet has to go to address 192.168.0.1, how would it know whether it should go to your wireless router or to eth1 of the server ? 

> **dinodom000 said:**
> 
Being that the servers dhcp ranges from 198.168.0.100-200 i would assume the routers external address would be 198.168.0.100 as it will be the only device.
Your dhcp server might just as well pick any address between 100 and 200 and assign that to the router.

---

### Post by LinuxRules1 on 2009-05-24
Make sure you set the /etc/default/dhcp3-server file to listen to the eth1 device. just edit the line that looks like this

INTERFACES=""

and make it look like this

INTERFACES="eth1"

---

### Post by dinodom000 on 2009-05-24
> **koenn said:**
> And if a packet has to go to address 192.168.0.1, how would it know whether it should go to your wireless router or to eth1 of the server ?
eth1 of the servers ip is 192.168.0.1, and the ip im trying to assign to the router is 192.168.0.100-200. The 192.168.0.1 is what the routers gateway is for computers that connect to it.

> Your dhcp server might just as well pick any address between 100 and 200 and assign that to the router.

It shouldn't matter what it gets should it?

---

### Post by dinodom000 on 2009-05-24
> **LinuxRules1 said:**
> Make sure you set the /etc/default/dhcp3-server file to listen to the eth1 device. just edit the line that looks like this

INTERFACES=""

and make it look like this

INTERFACES="eth1"

I already have it set to listen on eth1. I wish i didn't though and this problem would be fixed! Thanks though.

---

### Post by LinuxRules1 on 2009-05-24
The only thing that i can think of now is that there is a syntax error in your dhcpd.conf file.

---

### Post by koenn on 2009-05-25
> **dinodom000 said:**
> eth1 of the servers ip is 192.168.0.1, and the ip im trying to assign to the router is 192.168.0.100-200. The 192.168.0.1 is what the routers gateway is for computers that connect to it.



It shouldn't matter what it gets should it?

You may need to add a static route further down the line (whether or not this is the case depends on what you're trying to do, but it's likely), and setting static routes to an unpredictable router address is kind of a pain in the lower part of the back.

---

### Post by dinodom000 on 2009-05-28
I can set the router to be use DHCP to get its ip address, shouldn't that work fine? Just to test the dhcp3 server i hooked the server to the internet on eth0 and to a hub on eth1 and on the hub i hooked up a laptop and it still didn't work. I just can't see a reason why it doesn't work... im completely confused and frustrated now. :(

---

### Post by LinuxRules1 on 2009-05-28
> **dinodom000 said:**
> I can set the router to be use DHCP to get its ip address, shouldn't that work fine? Just to test the dhcp3 server i hooked the server to the internet on eth0 and to a hub on eth1 and on the hub i hooked up a laptop and it still didn't work. I just can't see a reason why it doesn't work... im completely confused and frustrated now. :(

Try using this as your dhcpd.conf file. It is the same format as the one that i use for my dhcp server (ubuntu 8.10). I edited it to match the settings that you want. I hope this will work.

```

ddns-update-style interim;
ignore client-updates;
allow booting;
allow bootp;
option option-128 code 128 = string;
option option-129 code 129 = text;
subnet 192.168.0.0 netmask 255.255.255.0 {
	# --- default gateway
	option routers 192.168.0.1;
	option subnet-mask 255.255.255.0;
	option nis-domain "network";
	option domain-name "network";
	option domain-name-servers 208.67.222.222, 208.67.220.220;
	option time-offset -18000;
	next-server 192.168.0.1;
	filename "pxelinux.0";
	range dynamic-bootp 192.168.0.100 192.168.1.200;
	default-lease-time 86400;
	max-lease-time 604800;
	}

```

---

### Post by dinodom000 on 2009-05-30
It did! I replaced my script with that and it worked great! Gave my router ip 192.168.0.101 (I tested it on my laptop first and that one reserved 100) But now my only problem is that it doesn't forward the internet connection. Any suggestions?

---

### Post by LinuxRules1 on 2009-05-31
I use a firewall program called firestarter to forward the internet connection on my dhcp server.

---

### Post by dinodom000 on 2009-06-05
Thanks for all your help! I have everything working as it should. And just one question when i start setting up servers do i need to do port forwarding with iptables?

Also how would i get all web traffic to run through the caching proxy (squid)?

---

