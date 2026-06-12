---
title: "Server DHCP3  has stopped to give addresses"
date: 2011-03-07
forum: Server Platforms
---

### Post by aigore on 2011-03-07
Hi all, I'm writing because my ubuntu server has started with troubles :(.
It's running Linux 2.6.32-29-generic-pae kernel for ubuntu server 10.04 and after the last update it stopped from giving addresses on clients connected.
Dhcp3 server it's running and the conf files are fine, but i can only use static addresses assignation now...
Also MYSQL has stopped working (installed for Bacula purpose) but now the dhcp problem is the biggest issue. I work in an office where dhcp is fundamental, too much clients (about 15) that are personal laptops also (so static assignation for clients is not a good choose).
Please any one could help me? It's two days I'm trying to figure it out without success. 
also tried removing and reinstalling dhcp3-serer...no way.
Here are my conf files


DHCPD.conf
```
#

ddns-update-style none;

option domain-name "semintesta";
option domain-name-servers 62.101.93.101, 83.103.25.250;

default-lease-time 600;
max-lease-time 7200;
log-facility local7;

#eth0 config
subnet 192.168.0.0 netmask 255.255.255.0 {
	authoritative;
	option routers 192.168.0.2;
	option broadcast-address 192.168.0.255;
	option netbios-name-servers 192.168.0.2;
	range 192.168.0.100 192.168.0.250;
	# mostro	
	host mostro {
		hardware ethernet 00:1e:8c:1a:2a:cb;
		fixed-address 192.168.0.222;
		}
	# access point net gear
	host Ap-netgear {
		hardware ethernet 00:18:4D:E0:6B:64;
		fixed-address 192.168.0.229;
		}
	# mail
	host mail {
		hardware ethernet 00:11:d8:58:47:ed;
		fixed-address 192.168.0.223;
		}
	# mailwifi
	host free-desktop {
		hardware ethernet 00:1e:2a:bc:62:a2;
		fixed-address 192.168.0.230;
		}
	# RoamaboutAP
	host RoamaboutAP {
		hardware ethernet 00:11:88:05:74:2e;
		fixed-address 192.168.0.206;
		}
	# stampantona
	host stampantona {
		hardware ethernet 00:C0:EE:D2:59:4C;
		fixed-address 192.168.0.217;
		}
	# vincio
	host vince {
	hardware ethernet 00:1f:e2:a4:4a:e0;
	fixed-address 192.168.0.211;
	}
	}


```

/etc/default/dhcp3-server
```
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"

```


/etc/network/interfaces 
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
post-up iptables-restore < /etc/iptables.up.rules

```

cat /etc/host
```
 
127.0.0.1	localhost
127.0.1.1	server	server
192.168.0.2	server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

Another strange behaviour is that my shell doesn't keep the command history.....mmmmm....weird

Thank you in advance!

---

### Post by terazen on 2011-03-08
Check /var/log/syslog after restarting dhcp.  Usually there is something explanatory about why no leases were given.

---

