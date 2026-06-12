---
title: "How to set default gateway for internet/vpn"
date: 2010-06-28
forum: Server Platforms
---

### Post by Nessaja on 2010-06-28
Hi,
 
I'm having some difficulty with a internet/vpn setup.
I have 3 network adapters on the server.
1x is used to connect it to the rest of the network
1x is used to provide internet (squid,dansguardian)
1x is used to connect to the vpn router
 
My interfaces file looks like this:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface

auto eth0 #Connecion to internet router
iface eth0 inet static
address 192.168.0.6
netmask 255.255.255.0
network 192.168.0.7/24
gateway 192.168.0.1
 
auto eth1 #Connection to Network switch
iface eth1 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0/24
gateway 192.168.0.6
 
auto eth2 #Connection to VPN Router
iface eth2 inet static
address 10.0.2.99
netmask 255.255.255.0
network 10.0.2.0/24
gateway 192.168.0.6
#gateway 10.0.2.2


```
 
The problem that I have is this: When the gateway on eth2 is set to 10.0.2.2 the VPN works 100% but there is no internet. When the gateway on eth2 is set to 192.168.0.6 there is internet but no VPN.
 
So what I want to do is, route all traffic that is supposed to go to 10.0.2.0/24 and 10.0.3.0/24 to eth2 and all internet traffic to eth0.
 
Is this even possible?

---

### Post by windependence on 2010-06-28
You can't do what you are trying to do. You can only have one gateway per system or as you have seen, things won't work. Think about how the system is supposed to know what gateway to use for what service.

-Tim

---

### Post by Nessaja on 2010-06-30
There has to be a way, there must be other companies that tried the same?
 
Even if I use more than one PC to do the VPN I'll still have the same problem.
 
Let me describe it a bit simpler.
 
I've got 1 PC, 2 routers connected to it.
 
LAN CARD 1 = Goes to network switch where all the other pcs are connected
                      192.168.1.1
 
LAN CARD 2 = Goes to router that supplies internet
                      192.168.0.1
 
LAN CARD 3 = Goes to router that supllies VPN
                      172.31.1.1
 
All I want to do is make it possible for the computers connected to LAN CARD 1 (the internal network) to be able to see all computers connected to the 172.31.1.0/24 network on LAN CARD 3, but must still be able to have internet connectivity using LAN CARD 2

---

### Post by spynappels on 2010-06-30
You could always leave the Internet router as the default gateway and use static routes to tell clients that nodes on the VPN can be reached through the VPN Router interface (LAN card 2) IP Address.

---

### Post by Groodles on 2010-07-01
Windependence is correct.  A machine does not like having more than one gateway.

However, what you want to do is possible, it's just a question of modifying the route table on the server to do what you want.

Obviously all local network clients will need to use the server as "their" default gateway.

Please paste the output of

```
sudo route
```

---

### Post by Nessaja on 2010-07-07
Sorry for taking so long to respond, had some conectivity issues
 
Here is the current route
 
 
```

[EMAIL="root@ec-squid:/home/squid"]root@ec-squid:/home/squid[/EMAIL]# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.2.0        *               255.255.255.0   U     0      0        0 eth2
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
10.0.3.0        Billion.400G    255.255.255.0   UG    0      0        0 eth2
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth0



```
 
I used route add -net
 
 
the Billion.400G is used for the VPN and the 192.168.0.1 is the cisco for internet.
VPN changed to 10.0.2.0/24 for this site and 10.0.3.0/24 for remote side
 
The internal network range is 192.168.1.0/24 and should be able to see the 10.0.2.0/24 range thats connected to the VPN solution
The linux pc can now ping the 10.0.3.0/24 network, but, any pc connected to the linux proxy can't ping that network, should I add the route on every connected pc?
or can I use iptables to do the routing?

---

### Post by Nessaja on 2010-07-07
Okay, I think I've figured it out,
with the following line iptables -t nat -A POSTROUTING -o eth2 -j MASQUERADE
it seems to work, I can now ping the router on the other side from any internal pc.
 
I'll keep you posted though

---

