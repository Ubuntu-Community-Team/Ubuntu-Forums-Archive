---
title: "Network Problems KVM and ubuntu server"
date: 2011-11-07
forum: Server Platforms
---

### Post by senjin on 2011-11-07
Hi 
I am running a kvm setup on my home server that is supposed to work as a router. 
I am running with three nics two intel nics dedicated to the virtual pfsense router and the onbord nic that is dedicated to the server itself and in turn connected via a switch to the pfsense nics. 

The problem is that the server can't connect to the internet. It can ping other hosts on my network and the windows computers and my android phone on the network can browse the web. But my freshly installed ubuntu laptop can't.

Is this a problem with the router or a problem with the network configs on my computers?

sorry for bad gramar etc

---

### Post by Jonathan L on 2011-11-07
> **senjin said:**
> Hi 
I am running a kvm setup on my home server that is supposed to work as a router. 
I am running with three nics two intel nics dedicated to the virtual pfsense router and the onbord nic that is dedicated to the server itself and in turn connected via a switch to the pfsense nics. 

The problem is that the server can't connect to the internet. It can ping other hosts on my network and the windows computers and my android phone on the network can browse the web. But my freshly installed ubuntu laptop can't.

Is this a problem with the router or a problem with the network configs on my computers?

sorry for bad gramar etc

Hi Senjin

I've understood your network to be like this (with made-up IP addresses), with nics 1 and 2 being used by the pfsense virtual, and nic0 the server itself.
```
        public
         |
         |
+--------*--+
|       nic2|
| nic0  nic1|
+--*-----*--+
   |.32  |.1
   |     |
+==*=====*=====*=======*=====+
               |.128   |.129
               |       |
             +-*-+   +-*-+
             |win|   |ubu|
             +---+   +---+
```Things to check:

[LIST=1]
[*] what is the default route of the server and the laptop ubu?
[*] can the server ping the bottom side router ip address?
[*] Can the laptop ping them?
[*] what is the default route of the windows machine?
[/LIST]
 
Hope that's of some help: write back with the results and let us know how you get on.

Kind regards,
Jonathan.

---

### Post by senjin on 2011-11-07
> **Jonathan L said:**
> Hi Senjin

I've understood your network to be like this (with made-up IP addresses), with nics 1 and 2 being used by the pfsense virtual, and nic0 the server itself.
```
        public
         |
         |
+--------*--+
|       nic2|
| nic0  nic1|
+--*-----*--+
   |.32  |.1
   |     |
+==*=====*=====*=======*=====+
               |.128   |.129
               |       |
             +-*-+   +-*-+
             |win|   |ubu|
             +---+   +---+
```Things to check:

[LIST=1]
[*] what is the default route of the server and the laptop ubu?
[*] can the server ping the bottom side router ip address?
[*] Can the laptop ping them?
[*] what is the default route of the windows machine?
[/LIST]
 
Hope that's of some help: write back with the results and let us know how you get on.

Kind regards,
Jonathan.

Thanks for the quick reply

[LIST=1]
[*] what is the default route of the server and the laptop ubu?
I get two default routes with netstat -rm one with dest 0.0.0.0 that has correct gateway (router ip) and one with dest 192.168.1.0 with gateway 0.0.0.0
[*] can the server ping the bottom side router ip address? 
Yes
[*] Can the laptop ping them?
Yes
[*] what is the default route of the windows machine?
router ip (192.168.1.1)
[/LIST]

I failed to mention that on the server there is a freenas vm running that is connected to the lan nic1 and it can connect to the internet 

my /network/interfaces looks like this
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
auto br0
iface br0 inet dhcp
        bridge_ports eth2
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

auto br1
iface br1 inet static
        address 192.168.1.1
        network 192.168.1.0
        netmask 255.255.255.0
        bridge_ports eth1
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```

---

### Post by senjin on 2011-11-08
The problem did fix itself when i asigned a static ip to the server it would seem that one of the switches in the network does not do it's job as it should.

I does however wonder if its possible to make a virtual connection to the server from the pfsense vm and then having three ports on the router.

---

### Post by Jonathan L on 2011-11-08
> what is the default route of the server and the laptop ubu?

[LIST=1]
[*] I get two default routes with netstat -rm one with dest 0.0.0.0 that has correct gateway (router ip) and one with dest 192.168.1.0 with gateway 0.0.0.0
[/LIST]
By "correct gateway" from what you've descibred I take it you mean 192.168.1.1.

NB the "gateway 0.0.0.0" just means it's local to the interface.

Glad it's resolved.

Kind regards,
Jonathan.

---

### Post by senjin on 2011-11-08
> **Jonathan L said:**
> By "correct gateway" from what you've descibred I take it you mean 192.168.1.1.

NB the "gateway 0.0.0.0" just means it's local to the interface.

Glad it's resolved.

Kind regards,
Jonathan.

It does however look like my mirth was a bit premature now the server connects to the internet but not to the router

---

