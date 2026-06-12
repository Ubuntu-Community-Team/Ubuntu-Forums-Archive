---
title: "Going KVM, bridging question."
date: 2010-02-01
forum: Server Platforms
---

### Post by DrJohn999 on 2010-02-01
Now I'm starting to migrate over to the a server, running Karmic. It's up and providing the basic networking services, but now I want to creat a pair of KVM VMs to host web services and a document server. I can allocate a fixed IP address for each. See attached image for an idea of one way to configure this.

I built a KVM virtual server instance, which is running, but I'm having some difficulty getting the bridging correct. Currently I have:
```
~# brctl show
bridge name	bridge id		STP enabled	interfaces
br0		8000.0026183b0b6e	no		eth0
virbr0		8000.000000000000	yes		

```
Here, virbr0 has no mac id and "showmacs" has no addresses, ie. it's not been intialized / started.
In /etc/network/interfaces, the physical interface eth0 appears as a port on the bridege br0:
```
~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto br0
iface br0 inet static
	address a.b.c.170
	netmask 255.255.255.0
	network a.b.c.0
	broadcast a.b.c.255
	gateway a.b.c.1
	bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

# Internal wired LAN interface
auto eth1
iface eth1 inet static
	address 192.168.2.1
	netmask 255.255.255.0
	network 192.168.2.0
	broadcast 192.168.2.255

# Internal wireless LAN interface
auto eth2
iface eth2 inet static
	address 192.168.3.1
	netmask 255.255.255.0
	network 192.168.2.0
	broadcast 192.168.3.255


```
virbr0 comes and goes from ifconfig: starting the VM brings it in, and restarting networking with the VM shutdown removes it. br0 persists.

Networking to/from eth1 and eth2 is working flawlessly; this is the bit labeled a.b.c.170 on the diagram. Haven't installed OpenVPN yet.

How do I get bridging configured so that I can talk to the new VM instance via ssh? (ssh_server was installed as part of the 'first boot' script, boot.sh). The VM was assigned one of the fixed IP addresses.

---

### Post by vpadro on 2010-02-02
I think you are missing this:

> 
auto lo
iface lo inet loopback

[b]auto eth0
iface eth0 inet manual[/b]

auto br0
iface br0 inet static
        address 192.168.0.10
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0


[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

---

### Post by DrJohn999 on 2010-02-02
Thanks, somehow I missed that one.

Next question, though, is this: The VM is running and I can establish an ssh session with it by talking to it's public IP. Having port 22 open on the public side isn't such a good idea, so I'd like to connect to the VM via a private subnet, but not the same as the already established 192.168.2/3. I see that adding another network is possible in the VM, but I can't find any coherent linear procedure to do so.

Also, how do I establish a console session with the VM? In virsh? That's not particularly clear either.

Anyone know where I can find this information?

Thanks!

---

### Post by DrJohn999 on 2010-02-03
Found some answers. For communications, used this zone file in Shorewall:
```
#ZONE	INTERFACE	BROADCAST	OPTIONS
net     br0              detect          bridge,tcpflags,nosmurfs,routefilter,logmartians
net	eth0		detect		bridge,tcpflags,nosmurfs,routefilter,logmartians
loc     eth1             detect          dhcp,tcpflags,nosmurfs,routefilter,logmartians
loc	eth2  		detect		dhcp,tcpflags,nosmurfs,routefilter,logmartians
dmz	vnet0		detect		bridge,tcpflags,nosmurfs,routefilter,logmartians

```
The trick was to define both eth0 and br0 in the net zone. Be sure to set appropriate rules for example (just a partial of the entire set but you get the idea):
```
Web/ACCEPT	dmz		net
Web/ACCEPT	loc		dmz
Web/ACCEPT	$FW		dmz

```

The console tty0 question appears to be answered here: [http://viz.is-a-geek.com/~viz/cw/index.php?KVM#q58fb4f1]("http://viz.is-a-geek.com/~viz/cw/index.php?KVM#q58fb4f1"). I'll give it a try soon...

---

