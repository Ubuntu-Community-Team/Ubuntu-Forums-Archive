---
title: "Problems with DNS or is it dhcp - not too sure?"
date: 2011-08-08
forum: Server Platforms
---

### Post by g0lrk on 2011-08-08
I've got Ubuntu Server 10.04.03 i386 on a home set-up hopefully going to run in the background as an internet/print/samba/security server for the family here.
I've tried numerous distros and all seem to have the same problem, so must be pointing to the way I'm installing them so here we go!
The server is in an outbuilding about 30 foot or so away from the house, in the same building is the adsl.
That connects to one network card, then the other network card goes to a TP 5 port switch.
From here it feeds 1 computer in the same building running LinuxMint9,[with an all-in-one printer attached].
Then one feed goes the 30 feet to the house and then inside about another 15/20 feet to a Belkin router that feeds one computer wired, Mint9, and 1 laptops with Mint9 and one notebook with Ubuntu 9, both wireless.
The problem is though that the server is not giving out dhcp to anything at all.
I have tried with and without the switch, though I need that to distribute the 'net around from the server.
There is another matter on top of this about a teenager and the net, I need to be able to police the sites visited, and edit them accordingly - yes I know all about squid and the like but the teenager is very  savvy indeed!

More info if needed of course but there's a bit below to start & you can see my dilemma folks, so can anyone help me please?

```
uname -a --
Linux buntu-160 2.6.32-33-generic-pae #71-Ubuntu SMP Wed Jul 20 18:46:41 UTC 2011 i686 GNU/Linux


route -n --
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

ifconfig --
eth0      Link encap:Ethernet  HWaddr 00:19:db:ab:7e:3c  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:feab:7e3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10522 (10.5 KB)  TX bytes:16925 (16.9 KB)
          Interrupt:23 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:14:c1:4b:ba:49  
          inet addr:192.168.1.75  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:c1ff:fe4b:ba49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:466 dropped:0 overruns:0 frame:0
          TX packets:191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:23355 (23.3 KB)
          Interrupt:18 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10345 (10.3 KB)  TX bytes:10345 (10.3 KB)

/etc/resolv.conf --
nameserver 192.168.1.1

/etc/network/interfaces --
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.70
	netmask 255.255.255.0
	gateway 192.168.1.1

auto eth1
iface eth1 inet static
	address 192.168.1.75
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255

/etc/dhcp3/dhcpd.conf --


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
option domain-name "buntu-160";
option domain-name-servers 192.168.1.1;

default-lease-time 86400;	# 24 hours ish!
max-lease-time 172800;		# 48 hours ish!

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;
	option subnet-mask 255.255.255.0;
	option broadcast-address 192.168.1.255;
	option routers	192.168.1.1;
	option domain-name-servers	192.168.1.1;
	option domain-name "buntu-160";
	subnet 192.168.1.0 netmask 255.255.255.0 {
	range 192.168.1.80 192.168.1.100;
}

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

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

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}


```

---

### Post by Bachstelze on 2011-08-08
If I were you, I would just add another "stock" router on top of the server. It is generally considered bad practice to run services on a router.

If you really want to use the server as a router, both interfaces are on the same subnet. That is probably not what you want. Also I recommend using dnsmasq for DHCP and DNS sharing.

---

### Post by sanderj on 2011-08-08
I don't understand your (topological) description, but I do see this:

```

eth0      Link encap:Ethernet  HWaddr 00:19:db:ab:7e:3c  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0

<snip>

eth1      Link encap:Ethernet  HWaddr 00:14:c1:4b:ba:49  
          inet addr:192.168.1.75  Bcast:192.168.1.255  Mask:255.255.255.0

```

That's probably illegal (you can't have two different connected networks with the same subnet), and if not, probably useless: If you want to have two different networks, you need to have different subnets, for example 192.168.1.x and 192.168.2.x

But do you really need two different networks? It's not fun unless you really know what to do.

And another rule of thumb: modems/routers are much easier to set up to be DHCP server than a Linux machine.

So: why the different networks?

---

### Post by g0lrk on 2011-08-09
**Bachstelze** The reason I'm doing it this way and not just with a 'stock' router on top of the server is that I feel that I can get more control re. the teenager angle if you know what I mean! But thanks for the input though!

**sanderj** As both you and **Bachstelze** said I never knew that it was bad practice to have both cards on the same subnet, whilst being two different networks?
That has now been changed with eth1 now being given the address of 
192.168.2.75  Bcast:192.168.2.255  Mask:255.255.255.0

I have changed this in /etc/network/interfaces & /etc/dhcp3/dhcpd.conf,
also changing the range in there accordingly, this on restarting gives the correct ip expected, but still no dhcp is issued on connecting either a laptop or other computer.
Here's my latest start-up log.
Cheers to everyone out there helping I do appreciate it.
Kevin.
```
Aug  9 10:22:02 buntu-160 cron[810]: (CRON) STARTUP (fork ok)
Aug  9 10:22:02 buntu-160 named[804]: listening on IPv4 interface lo, 127.0.0.1#53
Aug  9 10:22:02 buntu-160 named[804]: listening on IPv4 interface eth1, 192.168.2.75#53
Aug  9 10:22:02 buntu-160 named[804]: listening on IPv4 interface eth0, 192.168.1.70#53
Aug  9 10:22:02 buntu-160 named[804]: generating session key for dynamic DNS
Aug  9 10:22:02 buntu-160 named[804]: automatic empty zone: 254.169.IN-ADDR.ARPA
Aug  9 10:22:02 buntu-160 named[804]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Aug  9 10:22:02 buntu-160 named[804]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Aug  9 10:22:02 buntu-160 named[804]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Aug  9 10:22:02 buntu-160 named[804]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Aug  9 10:22:02 buntu-160 named[804]: automatic empty zone: D.F.IP6.ARPA
Aug  9 10:22:02 buntu-160 named[804]: automatic empty zone: 8.E.F.IP6.ARPA
Aug  9 10:22:02 buntu-160 named[804]: automatic empty zone: 9.E.F.IP6.ARPA
Aug  9 10:22:02 buntu-160 named[804]: automatic empty zone: A.E.F.IP6.ARPA
Aug  9 10:22:02 buntu-160 named[804]: automatic empty zone: B.E.F.IP6.ARPA
Aug  9 10:22:02 buntu-160 cron[810]: (CRON) INFO (Running @reboot jobs)
Aug  9 10:22:02 buntu-160 named[804]: command channel listening on 127.0.0.1#953
Aug  9 10:22:02 buntu-160 named[804]: command channel listening on ::1#953
Aug  9 10:22:02 buntu-160 named[804]: zone 0.in-addr.arpa/IN: loaded serial 1
Aug  9 10:22:02 buntu-160 named[804]: zone 127.in-addr.arpa/IN: loaded serial 1
Aug  9 10:22:02 buntu-160 named[804]: /etc/bind/zones/rev.1.168.192.in-addr.arpa:1: no current owner name
Aug  9 10:22:02 buntu-160 named[804]: zone 1.168.192.in-addr.arpa/IN: loading from master file /etc/bind/zones/rev.1.168.192.in-addr.arpa failed: no owner
Aug  9 10:22:02 buntu-160 named[804]: zone 1.168.192.in-addr.arpa/IN: not loaded due to errors.
Aug  9 10:22:02 buntu-160 named[804]: zone 255.in-addr.arpa/IN: loaded serial 1
Aug  9 10:22:02 buntu-160 named[804]: /etc/bind/zones/buntu-160.db:1: unknown RR type 'Replace'
Aug  9 10:22:02 buntu-160 named[804]: zone buntu-160/IN: loading from master file /etc/bind/zones/buntu-160.db failed: unknown class/type
Aug  9 10:22:02 buntu-160 named[804]: zone buntu-160/IN: not loaded due to errors.
Aug  9 10:22:02 buntu-160 named[804]: zone localhost/IN: loaded serial 2
Aug  9 10:22:02 buntu-160 named[804]: running
Aug  9 10:22:02 buntu-160 dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Aug  9 10:22:02 buntu-160 dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Aug  9 10:22:02 buntu-160 dhcpd: All rights reserved.
Aug  9 10:22:02 buntu-160 dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Aug  9 10:22:02 buntu-160 dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Aug  9 10:22:02 buntu-160 dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Aug  9 10:22:02 buntu-160 dhcpd: All rights reserved.
Aug  9 10:22:02 buntu-160 dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Aug  9 10:22:02 buntu-160 dhcpd: Wrote 0 leases to leases file.
Aug  9 10:22:03 buntu-160 avahi-daemon[707]: Server startup complete. Host name is buntu-160.local. Local service cookie is 835894948.
Aug  9 10:22:03 buntu-160 /etc/mysql/debian-start[874]: Upgrading MySQL tables if necessary.
Aug  9 10:22:03 buntu-160 /etc/mysql/debian-start[877]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Aug  9 10:22:03 buntu-160 /etc/mysql/debian-start[877]: Looking for 'mysql' as: /usr/bin/mysql
Aug  9 10:22:03 buntu-160 /etc/mysql/debian-start[877]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Aug  9 10:22:03 buntu-160 /etc/mysql/debian-start[877]: This installation of MySQL is already upgraded to 5.1.41, use --force if you still need to run mysql_upgrade
Aug  9 10:22:03 buntu-160 /etc/mysql/debian-start[884]: Checking for insecure root accounts.
Aug  9 10:22:03 buntu-160 /etc/mysql/debian-start[888]: Triggering myisam-recover for all MyISAM tables
Aug  9 10:22:04 buntu-160 kernel: [   10.981901] ppdev: user-space parallel port driver
Aug  9 10:22:05 buntu-160 ntpdate[1005]: step time server 91.189.94.4 offset 0.001565 sec
Aug  9 10:22:11 buntu-160 kernel: [   17.544006] eth0: no IPv6 routers present
Aug  9 10:22:11 buntu-160 kernel: [   17.572004] eth1: no IPv6 routers present
```

---

### Post by sanderj on 2011-08-09
Some remarks:

Have you setup routing between the two subnets?
Why are you running named / DNS? You very probably don't need that. Named with it's own zones is a first-class headache.
Setting up a DHCP server on Ubuntu: I think a Google search will help you.

But, as said in my earlier post, I would advice you not to use two subnets nor a separate DHCP server. Let your modem/router take care of it.

---

### Post by remmargorp on 2011-08-09
He's probably running named to act as a local caching server (why not?)


Topology appears to be as follows

ADSL Modem --> SERVER NIC 1 --> SERVER --> SERVER NIC 2 --> TP SWITCH --> BELKIN ROUTER --> PC/LAPTOPS (wired/wireless)


My assumption is you're trying to have the server act as a router between the ADSL modem and the client side (TP switch to PC's), hence the two NIC's on different subnets.

Can you define what the TP switch is? (I'm used to TP being TippingPoint, I doubt that is what you are referring to, most like just a basic 5 port switch)

Is the uplink to the Belkin router connecting to its WAN or LAN port?

Are you trying to serve DHCP from the linux server to the PC/LAPTOPS?


Paste the results of the following:
cat /etc/network/interfaces
cat /etc/dhcp3/dhcpd.conf | grep -e "^[^#]"
netstat -nr


- Your first step should be to confirm your topology (and how you would expect traffic to route, connections to your Belkin router, etc)
- Your next step would be to enable routing (assign static IPs to your test PC/laptop, make sure the server is configured to route traffic, test routing through the server to the ADSL modem/internet, etc)
- Your next step would be to install/configure and test DHCP (to avoid assigning static IPs)


I would suggest you look at Untangle (I know you probably want to get everything working yourself) but Untangle will do what you want and more

---

### Post by g0lrk on 2011-08-10
**sanderj** No I haven't setup routing between the two subnets - I wasn't aware of that at all sorry? How do you do that if it is needed please? 
I already did a Google search re DNS and it threw this link which I followed - [http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html]("http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html") the reason was as **remmargorp** says as a caching server and because in my 'infinite wisdom' I believed after reading many pages on Google it would be the best way to go for a home-server, [most probably wrong - right!].
Re letting the modem/router once again I 'thought' that given the teenager problem and wanting to be able to monitor that situation I 'thought' again that the server option was much better!

**remmargorp** the topology is 90% right with one computer connected to the TP switch as well as the cable in to the house!

The TP Switch is this one [http://www.tp-link.com/en/products/details/?categoryid=1585&model=TL-SG1005D]("http://www.tp-link.com/en/products/details/?categoryid=1585&model=TL-SG1005D") & the Belkin router is this one [http://www.belkin.com/uk/support/article/?lid=enu&pid=F5D7234uk4&aid=14386&scid=0]("http://www.belkin.com/uk/support/article/?lid=enu&pid=F5D7234uk4&aid=14386&scid=0")
To answer your question re which port the cable is connected to it is connected to the yellow one [WAN?], just an aside the ip of the Belkin is set at the moment to 192.168.3.1 
Next question would be yes my aim is to serve DHCP from the server to the PC/LAPTOPS/Wii/Whatever?

I have assigned a static IP of 192.168.1.85 to one Laptop to be a test laptop, with hope?

I have downloaded Untangle and at this moment in time I am burning to cd to try it on a spare hd in the server - just in case it does work as well as you say - I hope it does?

I hope that's answered a few questions, and thanks in advance for sticking with it.

Kevin.

```
cat /etc/network/interfaces:-

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.2.1
	netmask 255.255.255.0
	 gateway 192.168.1.1

auto eth1
iface eth1 inet static
	address 192.168.1.75
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255

cat /etc/dhcp3/dhcpd.conf | grep -e "^[^#]":-

ddns-update-style none;
option domain-name "buntu-160";
option domain-name-servers 192.168.2.1;
default-lease-time 86400;	# 24 hours ish!
max-lease-time 172800;		# 48 hours ish!
authoritative;
log-facility local7;
	option subnet-mask 255.255.255.0;
	option broadcast-address 192.168.1.255;
	option routers	192.168.1.1;
	option domain-name-servers 192.168.2.1;
	option domain-name "buntu-160";
	subnet 192.168.1.0 netmask 255.255.255.0 {
	range 192.168.1.80 192.168.1.100;
}

netstat -nr:-

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
```

---

### Post by sanderj on 2011-08-10
Enable routing / forwarding on Linux:

echo "1" > /proc/sys/net/ipv4/ip_forward

Does your ADSL-modem know that both 192.168.1.x and 192.168.2.x are on it's LAN interface? If not, the ADSL-modem will drop traffic. As a solution, you could let your Linux machine do NAT. 

Have you read [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router) ?

And have you read the last sentence in my previous post ... ? ;)

---

### Post by imortalninja161 on 2011-08-10
DHCP= Dynamic Host Configuration Protocol meaning the server will give out ip addresses as needed by clients and devices 

DNS=Domain Name Service  This is responsible for domain name resolution

Example you are going to a web page the computer has a name but No ip address and a ip address is needed to go to that web site so the server looks up that word or words and gets the ip address form that web page and in return you can access the web page.

having said that i don't understand why you need  ether of these to be manually configured by yourself in a simple home environment  having said that if you want a linux based server download Centos :D.

considering this is the topology


> Topology appears to be as t

ADSL Modem --> SERVER NIC 1 --> SERVER --> SERVER NIC 2 -->  TP SWITCH --> BELKIN ROUTER --> PC/LAPTOPS (wired/wireless)
why not connect ADSL modem to router then switch then all other devices.

so then all you need to do is make sure all devices have the router/modem as the default gateway as default route  and make sure the router has DNS and DHCP enabled Even if you you could make the Router say ipV4 address 10.0.0.1 255.0.0.0 then all othere devices PC1 10.0.0.2 255.0.0.0 default gateway 10.0.0.1 PC2 10.0.0.3 255.0.0.0 default gateway 10.0.0.1 ect....

It is True that routers are responsible for connecting different networks together but if that router has multiple Ethernet ints like fa0/0 fa0/1 fa0/2 you can leave the switch alone and configure just the pc's

as for controlling your sons Internet access there has to be simpler ways to control it try googling alternatives there has to be some type of web browser addon you can admin to control his page access. 

servers can be very messy if your not trained no offence man you can learn it just takes a very long time

---

### Post by g0lrk on 2011-08-10
**sanderj** Yes I have enabled routing / forwarding as you typed, also I've edited the line in I think /etc/sysctl.conf?
Re. 'not to use two subnets nor a separate DHCP server. Let your modem/router take care of it.' Not using two subnets I don't know any better - seriously, what else can I do to connect the system up the way it is?
The separate DHCP server, I was, but this is now in cloud cuckoo land for me - thinking of making a virtual DHCP server on this system, but in all honesty I don't think as a small home-set up it warrants it.
Or are you saying don't bother at all with anything and just use the router and the likes of squid to sort the 'net out for the teenager?
If that's the case I don't really know what to do??

Anyone got a couple of wires spare and a bit of electric they can loan me :)

**imortalninja161** Thanks for your explanation of DNS & DHCP that makes it dead easy for me to understand, cheers!

As for putting the modem/router and the Belkin router both next to each other well, the server & modem/router is in a out-building about 45/50 feet away from the Belkin router, so it's really difficult. That's where the electrical string comes in handy to connect them up 8)

**remmargorp** I've downloaded that Untangle you mentioned but for some reason it will not install correctly here?
I know it's a Debian based distro and normally I have no worries with them on that machine, it's an old desktop I've had a while, but it just will not fully install?
I've changed the video card, network card, memory, monitors, hard drives and no joy after trying 8 times so I've given up on it after reviewing a few posts on their Forum[s]. Thanks a lot anyway though.

OK thanks to everyone so far.
Cheers.
Kevin

---

### Post by g0lrk on 2011-08-29
Well no-one came forward with the answer to my problem?
So............

I went and downloaded another distro [http://wiki.contribs.org/SME_Server:Download]("http://wiki.contribs.org/SME_Server:Download")
which I was very surprised at because after about half a dozen or so questions it worked!

Now that proved to me that my computer components individually would all work together, and it gave me renewed vigour to get Ubuntu server to do so.

So with that aim in mind here I am again.....

Right as the physical set-up as not changed as per my original post please refer back to there for that set-up. 

I have re-installed, many times since and have now got to the stage where it is issuing a dhcp lease but, I am unable to get on to the internet from any machine on the lan? 

I have in essence, with changes to suit my set-up followed roughly from [http://ubuntuforums.org/showpost.php?p=9976398&postcount=6]("http://ubuntuforums.org/showpost.php?p=9976398&postcount=6") 

And yes I have echo "1" > /proc/sys/net/ipv4/ip_forward and edited the same in /etc/sysctl.conf.

Also I've added the following:-
```
ip route add 192.168.223.0/24 dev eth1
ip route add 192.168.1.0/24 dev eth0
ip route add default via 192.168.1.1

```
As I read on this Forum that this was also needed, [a little knowledge is a dangerous thing!]

So there you are could somebody offer help please as when I connect a machine via the lan it doesn't connect to the net as I require it to do, and instead turns it toes up.

I have searched quite extensively on this Forum and on google and re-installed many times indeed now.

Thanks to you for reading this diatribe and I look forward to your help, hopefully!

Cheers.
Kevin.

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.223.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.155
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1 208.67.222.222 208.67.220.220
	dns-search wallzone.ham
	pre-up iptables-restore < /etc/iptables.rules
	post.down iptables-save > /etc/iptables.rules

auto eth1
iface eth1 inet static
	address 192.168.223.15
	netmask 255.255.255.0
	network 192.168.223.0
	broadcast 192.168.223.255

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:c1:4b:ba:49  
          inet addr:192.168.1.155  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:c1ff:fe4b:ba49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45948 (45.9 KB)  TX bytes:26145 (26.1 KB)
          Interrupt:18 Base address:0xd000 

eth1      Link encap:Ethernet  HWaddr 00:19:db:ab:7e:3c  
          inet addr:192.168.223.15  Bcast:192.168.223.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:feab:7e3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13066 (13.0 KB)  TX bytes:10784 (10.7 KB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:856 (856.0 B)  TX bytes:856 (856.0 B)

/etc/resolv.conf
search wallzone.ham
nameserver 192.168.1.1
nameserver 208.67.222.222
nameserver 208.67.220.220
# The format of this file is documented in the dhcpd.leases(5) manual page.
# This lease file was written by isc-dhcp-V3.1.3

/var/lib/dhcp3/dhcpd.leases
lease 192.168.223.20 {
  starts 0 2011/08/28 10:45:44;
  ends 0 2011/09/04 10:45:44;
  tstp 0 2011/09/04 10:45:44;
  cltt 0 2011/08/28 10:45:44;
  binding state active;
  next binding state free;
  hardware ethernet 00:24:1d:10:3d:48;
  client-hostname "minty9-desktop";
}
lease 192.168.223.21 {
  starts 0 2011/08/28 16:48:58;
  ends 0 2011/09/04 16:48:58;
  tstp 0 2011/09/04 16:48:58;
  cltt 0 2011/08/28 16:48:58;
  binding state active;
  next binding state free;
  hardware ethernet a4:ba:db:a9:ce:b7;
  client-hostname "g0lrk-Vostro-3700";
}
lease 192.168.223.20 {
  starts 1 2011/08/29 08:02:45;
  ends 1 2011/09/05 08:02:45;
  cltt 1 2011/08/29 08:02:45;
  binding state active;
  next binding state free;
  hardware ethernet 00:24:1d:10:3d:48;
  client-hostname "minty9-desktop";
}
lease 192.168.223.20 {
  starts 1 2011/08/29 08:29:12;
  ends 1 2011/09/05 08:29:12;
  cltt 1 2011/08/29 08:29:12;
  binding state active;
  next binding state free;
  hardware ethernet 00:24:1d:10:3d:48;
  client-hostname "minty9-desktop";
}

/etc/dhcp3/dhcpd.conf
authoritative;
INTERFACES="eth1";
ddns-update-style ad-hoc;

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.223.255;
option routers 192.168.223.15;
option domain-name "wallzone.ham"; 
option domain-name-servers 192.168.223.15; 
default-lease-time 604800;					# 	1 week I think?
max-lease-time 2419200;						#	1 month possibly if my maths is correct?
INTERFACES="eth1";

subnet 192.168.223.0 netmask 255.255.255.0 {
range 192.168.223.20 192.168.223.33; 

}
/var/log/syslog | grep -i dhcp | tail -n45
Aug 28 17:41:33 buntu-test dhcpd: 
Aug 28 17:41:33 buntu-test dhcpd: No subnet declaration for eth0 (192.168.1.155).
Aug 28 17:41:33 buntu-test dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 28 17:41:33 buntu-test dhcpd:    you want, please write a subnet declaration
Aug 28 17:41:33 buntu-test dhcpd:    in your dhcpd.conf file for the network segment
Aug 28 17:41:33 buntu-test dhcpd:    to which interface eth0 is attached. **
Aug 28 17:41:33 buntu-test dhcpd: 
Aug 28 17:48:57 buntu-test dhcpd: DHCPDISCOVER from a4:ba:db:a9:ce:b7 via eth1
Aug 28 17:48:58 buntu-test dhcpd: DHCPOFFER on 192.168.223.21 to a4:ba:db:a9:ce:b7 (g0lrk-Vostro-3700) via eth1
Aug 28 17:48:59 buntu-test dhcpd: if g0lrk-Vostro-3700.wallzone.ham IN A rrset doesn't exist add g0lrk-Vostro-3700.wallzone.ham 302400 IN A 192.168.223.21: timed out.
Aug 28 17:48:59 buntu-test dhcpd: DHCPREQUEST for 192.168.223.21 (192.168.223.15) from a4:ba:db:a9:ce:b7 (g0lrk-Vostro-3700) via eth1
Aug 28 17:48:59 buntu-test dhcpd: DHCPACK on 192.168.223.21 to a4:ba:db:a9:ce:b7 (g0lrk-Vostro-3700) via eth1
Aug 28 18:04:16 buntu-test dhcpd: Wrote 2 leases to leases file.
Aug 28 18:04:16 buntu-test dhcpd: 
Aug 28 18:04:16 buntu-test dhcpd: No subnet declaration for eth0 (192.168.1.155).
Aug 28 18:04:16 buntu-test dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 28 18:04:16 buntu-test dhcpd:    you want, please write a subnet declaration
Aug 28 18:04:16 buntu-test dhcpd:    in your dhcpd.conf file for the network segment
Aug 28 18:04:16 buntu-test dhcpd:    to which interface eth0 is attached. **
Aug 28 18:04:16 buntu-test dhcpd: 
Aug 29 08:47:27 buntu-test kernel: [    6.112262] type=1505 audit(1314604046.088:3):  operation="profile_load" pid=485 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug 29 08:47:27 buntu-test kernel: [    6.123278] type=1505 audit(1314604046.096:6):  operation="profile_replace" pid=493 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug 29 08:47:27 buntu-test kernel: [    6.128694] type=1505 audit(1314604046.104:9):  operation="profile_replace" pid=495 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug 29 08:47:27 buntu-test dhcpd: Wrote 2 leases to leases file.
Aug 29 08:47:27 buntu-test dhcpd: 
Aug 29 08:47:27 buntu-test dhcpd: No subnet declaration for eth0 (192.168.1.155).
Aug 29 08:47:27 buntu-test dhcpd: ** Ignoring requests on eth0.  If this is not what
Aug 29 08:47:27 buntu-test dhcpd:    you want, please write a subnet declaration
Aug 29 08:47:27 buntu-test dhcpd:    in your dhcpd.conf file for the network segment
Aug 29 08:47:27 buntu-test dhcpd:    to which interface eth0 is attached. **
Aug 29 08:47:27 buntu-test dhcpd: 
Aug 29 09:02:44 buntu-test dhcpd: DHCPREQUEST for 192.168.1.2 from 00:24:1d:10:3d:48 via eth1: wrong network.
Aug 29 09:02:44 buntu-test dhcpd: DHCPNAK on 192.168.1.2 to 00:24:1d:10:3d:48 via eth1
Aug 29 09:02:44 buntu-test dhcpd: DHCPDISCOVER from 00:24:1d:10:3d:48 (minty9-desktop) via eth1
Aug 29 09:02:45 buntu-test dhcpd: DHCPOFFER on 192.168.223.20 to 00:24:1d:10:3d:48 (minty9-desktop) via eth1
Aug 29 09:02:46 buntu-test dhcpd: if minty9-desktop.wallzone.ham IN A rrset doesn't exist add minty9-desktop.wallzone.ham 302400 IN A 192.168.223.20: timed out.
Aug 29 09:02:46 buntu-test dhcpd: DHCPREQUEST for 192.168.223.20 (192.168.223.15) from 00:24:1d:10:3d:48 (minty9-desktop) via eth1
Aug 29 09:02:46 buntu-test dhcpd: DHCPACK on 192.168.223.20 to 00:24:1d:10:3d:48 (minty9-desktop) via eth1
Aug 29 09:29:11 buntu-test dhcpd: DHCPREQUEST for 192.168.1.2 from 00:24:1d:10:3d:48 via eth1: wrong network.
Aug 29 09:29:11 buntu-test dhcpd: DHCPNAK on 192.168.1.2 to 00:24:1d:10:3d:48 via eth1
Aug 29 09:29:11 buntu-test dhcpd: DHCPDISCOVER from 00:24:1d:10:3d:48 (minty9-desktop) via eth1
Aug 29 09:29:12 buntu-test dhcpd: DHCPOFFER on 192.168.223.20 to 00:24:1d:10:3d:48 (minty9-desktop) via eth1
Aug 29 09:29:13 buntu-test dhcpd: if minty9-desktop.wallzone.ham IN A rrset doesn't exist add minty9-desktop.wallzone.ham 302400 IN A 192.168.223.20: timed out.
Aug 29 09:29:13 buntu-test dhcpd: DHCPREQUEST for 192.168.223.20 (192.168.223.15) from 00:24:1d:10:3d:48 (minty9-desktop) via eth1
Aug 29 09:29:13 buntu-test dhcpd: DHCPACK on 192.168.223.20 to 00:24:1d:10:3d:48 (minty9-desktop) via eth1
```

---

### Post by g0lrk on 2011-09-01
Bump.

In case anyone can offer any help to my last post please?

Cheers,

Kevin.

---

### Post by g0lrk on 2011-09-12
Bump.....

As I said a fortnight ago " I have now got to the stage where it is issuing a dhcp lease but, I am unable to get on to the internet from any machine on the lan? "

So I am still wondering if there is anyone that could please offer me any help on this matter?

Cheers,

Kevin.

---

### Post by Doug S on 2011-09-12
Post 6 shows a network diagram where the ADSL modem is connected to eth0 (I think it is that one). What I do not understand with this whole thread is why eth0 has a non-routable IP address (an RFC1918 address). I would have expected it to have a real WAN roubtable IP address. Is the ADSL modem actually also a router, such that it is providing the NAT to the outside world? Maybe your ISP does it this way, mine does not. My ADSL modem is just a modem.

---

### Post by g0lrk on 2011-09-13
**Doug S** I have added a .png of the front page of my modem/router if that tells you anything at all?

Re. having a Wan routable address it does but I changed it to 192.168.1.? to suit the set-up accordingly - is that correct or not?

I am nothing but a beginner and bow down to your experience.

Cheers.

Kevin.

---

### Post by Doug S on 2011-09-14
O.K. so the adsl modem is actually a modem and router. So it is O.K.

---

### Post by Doug S on 2011-09-14
You need to figure out why minty9-desktop is asking for 192.168.1.2 and get it to stop. (it does get a proper IP address later though)
I don't think 192.168.1.1 is a nameserver, so references that say it is should be deleted.
I don't think this will fix your problem, but it will make your setup less wrong.
Perhaps list the contents of iptables. "sudo iptables -v -x -n -L" or just "sudo iptables -L" if you prefer.

---

### Post by g0lrk on 2011-09-15
**Doug S** Well I did as you suggested and ran with > "sudo iptables -v -x -n -L" and was surprised that this appeared -

```
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination 
```

Which of course means, [even to me!] that nothing is being allowed either way!

So I shall now treat google as a best friend and try to seek help from there, again!

Cheers for the help so far.

Kevin.

---

### Post by SeijiSensei on 2011-09-15
> **g0lrk said:**
> **Doug S** Well I did as you suggested and ran with  and was surprised that this appeared -

```
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination 
```

Which of course means, [even to me!] that nothing is being allowed either way!

On the contrary, it means that everything is allowed.  The default policy for all three chains is ACCEPT.

---

### Post by elico on 2011-09-15
you need to add a masqarad option on the nat tables in order to make it work.
it's really recommended to manage this server for your ease of use with a software like "WEBMIN"

---

### Post by Doug S on 2011-09-16
Just for a test to see if things start working, you could use this command to add to your iptables:
```
sudo iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to 192.168.1.155

```It is not much of a worry that you have no firewall rules, because your adsl modem/router provides them. However, you should learn about this stuff.
There were some similar threads just the other day([here]("http://ubuntuforums.org/showthread.php?t=1842229&page=2") and [here]("http://ubuntuforums.org/showthread.php?t=1841465")), that ended up with many references.

---

### Post by g0lrk on 2011-09-17
**Doug S** First off ```
sudo iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to 192.168.1.155
``` was successful in giving me internet over the Lan so well done for that!

Just need what ever else goes with it to make it secure, as can reasonably be then I can get to the number one problem - sorting the internet out some way for the teenager to restrict the sites/review the sites.

**elico** I haven't had a lot of luck with webmin, but that was before the server was actually set-up correctly - so I will try again once that is done.

**SeijiSensei** My apologies for mis-reading the default policies, once again my ignorance is showing. :redface:

Cheers to all so far.

Kevin.

---

### Post by g0lrk on 2011-10-02
Well I've sorted this problem out in around about way by doing what was suggested to me in post #6 by **remmargorp** and trying [http://www.untangle.com/]("http://www.untangle.com/") again.

But this time determination made me get it working and I found out that for some obscure reason my Nvidia card was not being recognised at the time the screen actually got in to it's working screen. 
So I edited the kernel start-up deleting ut-video, which is the default, adding nomodeset, that allowed it to start and install - then I edited the file menu.lst and did a grub-update.

Job done!

Just got to get used to the OS now and I'm set.

As of now it is working 100% and is stopping the teenager from getting on the 'dodgy' sites, and I can edit the files to my heart's content when I find new sites to add.


Many thanks to everyone especially to **remmargorp** for bouncing me to Untangle in the first place.

Cheers.
Kevin.

---

