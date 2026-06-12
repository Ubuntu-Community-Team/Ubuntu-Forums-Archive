---
title: "interfaces file network bridge video streaming, one  works other is horrible"
date: 2009-11-04
forum: Virtualisation
---

### Post by sdowney717 on 2009-11-04
streaming to a dsm 320 media player
file is etc/network/interfaces

this one works really well running vmware server, tversity, xp

> #static on eth2, static on bridge br0
auto eth2
iface eth2 inet manual

auto br0
iface br0 inet static
        address 192.168.1.100
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth2
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off 


this one works awful with video streaming

> #static on eth2, static on bridge br0
auto eth2
iface eth2 inet manual

auto br0
iface br0 inet static
        address 192.168.1.100
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth2
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

so what are the different options to tweak this even better
and is there a good guide?

---

### Post by sdowney717 on 2009-11-04
[http://perlstalker.blogspot.com/2008/10/life-with-kvm-networking.html](http://perlstalker.blogspot.com/2008/10/life-with-kvm-networking.html)

> scott@scott-desktop:~$ brctl
Usage: brctl [commands]
commands:
	addbr     	<bridge>		add bridge
	delbr     	<bridge>		delete bridge
	addif     	<bridge> <device>	add interface to bridge
	delif     	<bridge> <device>	delete interface from bridge
	setageing 	<bridge> <time>		set ageing time
	setbridgeprio	<bridge> <prio>		set bridge priority
	setfd     	<bridge> <time>		set bridge forward delay
	sethello  	<bridge> <time>		set hello time
	setmaxage 	<bridge> <time>		set max message age
	setpathcost	<bridge> <port> <cost>	set path cost
	setportprio	<bridge> <port> <prio>	set port priority
	show      				show a list of bridges
	showmacs  	<bridge>		show a list of mac addrs
	showstp   	<bridge>		show bridge stp info
	stp       	<bridge> {on|off}	turn stp on/off

scott@scott-desktop:~$ brctl show
bridge name	bridge id		STP enabled	interfaces
br0		8000.00221554faa6	no		eth2


scott@scott-desktop:~$ brctl show br0
bridge name	bridge id		STP enabled	interfaces
br0		8000.00221554faa6	no		eth2


scott@scott-desktop:~$ brctl showstp br0
br0
 bridge id		8000.00221554faa6
 designated root	8000.00221554faa6
 root port		   0			path cost		   0
 max age		  12.00			bridge max age		  12.00
 hello time		   2.00			bridge hello time	   2.00
 forward delay		   9.00			bridge forward delay	   9.00
 ageing time		 300.01
 hello timer		   1.48			tcn timer		   0.00
 topology change timer	   0.00			gc timer		   2.48
 flags			


eth2 (1)
 port id		8001			state		     forwarding
 designated root	8000.00221554faa6	path cost		  19
 designated bridge	8000.00221554faa6	message age timer	   0.00
 designated port	8001			forward delay timer	   0.00
 designated cost	   0			hold timer		   0.48
 flags			

scott@scott-desktop:~$ 


---

### Post by sdowney717 on 2009-11-04
all i can think is that the network needed some delay wait time to respond, when set to 0, TVersity was having serious issues, the server would not run or shut off, not respond etc...

this works

bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

this does not work

bridge_fd 0
bridge_maxwait 0 
bridge_stp off

---

