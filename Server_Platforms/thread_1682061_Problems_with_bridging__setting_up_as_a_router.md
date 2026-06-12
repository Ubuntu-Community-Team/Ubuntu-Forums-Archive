---
title: "Problems with bridging / setting up as a router"
date: 2011-02-05
forum: Server Platforms
---

### Post by turbine2 on 2011-02-05
Hi all,
Got a fair bit further now and I think I'm stuck at the second to last hurdle now.
 
I have the following setup:-
 
Home network => ubuntu 10.10 eth1 eth2 pppoe link to ISP via wireless network
 
I have managed to set up most of the setup using [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
 
I've got all the way down to the part about NAT just above section 5 but now I've got stuck.
 
I know the pppoe link is working and if I ping something (e.g. google.com) from the server it responds as expected. If I ping a computer on the internal network from the server it also responds as expected. However if I configure a computer on the internal network to use the server as a gateway I don't get a response (request timed out). Tracert from the workstation to the external IP address pinged gets to the server internal network card and then stops.
 
I did a quick search on here and saw the posting about /proc/sys/net/bridge and the bridge-nf-* files but I've tried the for loop in that and I'm still in the same position.
 
Where should I be looking next?
 
My interfaces file
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
 
# The primary network interface (internal, built in NIC)
#auto eth1
#iface eth1 inet static
#       address 192.168.1.5
#       netmask 192.168.1.5
#       gateway 217.169.29.126
 
auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
 
# The secondry network interface (external, PCI card)
auto eth0
iface eth0 inet manual
 
#Set up the bridge
auto br0
iface br0 inet static
        address 192.168.1.5
        network 192.18.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        bridge-ports eth1 ppp0

```

---

### Post by turbine2 on 2011-02-05
Bingo, I've now fixed this.
 
The script file nat.sh lists the two interfaces as 
 
```

EXTIF="eth0"
INTIF="eth1"

```
 
I'd swapped eth0 with ppp0 but it also needed eth1 swapped with br0.
 
Now all I've got to do is set up the external to internal NAT and I'll be away.

---

