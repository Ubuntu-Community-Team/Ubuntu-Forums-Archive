---
title: "how to use a separate network for my db cluster"
date: 2015-02-03
forum: Server Platforms
---

### Post by skrite on 2015-02-03
hello all.

I have 4 servers running a galera cluster. Each machine has dual nics. 
I would like to set up the second network card so that the cluster will connect to each other on its own separate network. I would like one switch with only the database cluster on it.
However, i don't know where to even begin to look up how to do this. 
What would I use as a gateway if they are only connected by a switch?
That network would have no need to reach outside the LAN.

 Appreciate any help, thanks.

---

### Post by MAFoElffen on 2015-02-03
Think about that logically and physically. 

Each has 2 NICs. The servers connected to each other the one of their NIC's via a switch. If the cluster is configured to use a network address other than your main network, (which is also how you normally connect SANs) then that is phyiscally separate to the other NIC that os on another Network address and not physically connected to that switch.

The only way you could connect both NIC to the same switch and have them separated out, is if the switch was a layer 3 switch, like some of the Cisco switches I have, where it can partition out Layer 3 network addresses by IP. A normal switch is not smart enough to do that and just deals just with MAC addresses.

---

### Post by skrite on 2015-02-03
Oh, i am sorry, I meant that I want one NIC on one switch and the other NIC on the rest of the LAN. I want one switch to only have the four database computers connected to it.

---

### Post by SeijiSensei on 2015-02-03
Connect the machines to the switch using their second adapters, then give them each a static IP in their own subnet, like 192.168.50.0/24.  Linux will know to route packets for the other servers over the correct interface.  Don't specify a "gateway" for these adapters in /etc/network/interfaces.  The stanza for the first machine would look like this:
```

auto eth1
iface eth1 inet static
address 192.168.50.1
netmask 255.255.255.0
broadcast 192.168.50.255

```

---

### Post by skrite on 2015-02-03
Very very cool, thanks for your help

---

