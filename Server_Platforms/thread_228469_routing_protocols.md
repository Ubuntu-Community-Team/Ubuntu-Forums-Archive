---
title: "routing protocols"
date: 2006-08-03
forum: Server Platforms
---

### Post by MajorT on 2006-08-03
I have a server setup with 3 NICs and 3 PCs one connected to the network of each NIC. 
I can ping the PCs from the server but cannot ping the PCs to each other.
I have confirmed that the PCs can ping if I set them to the same network.
The server interfaces file contains
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 172.16.1.254
netmask 255.255.255.0

auto eth1
iface eth1 inet static
address 172.16.2.254
netmask 255.255.255.0

auto eth2
iface eth2 inet static
address 172.16.3.254
netmask 255.255.255.0

The PCs are on 172.16.1.129, 172.16.2.129 and 172.16.3.129
I can ping the server addresses from each of the PCs.

Anyone help me?
Regards, Major (thats my Christian name ;-) )

---

### Post by MajorT on 2006-08-03
Additional:
Is there some sort of default integrated firewall in the server that is stopping network traffic from passing between devices?
If so how do I disable it?
Please help if you can.
Regards, Major.

---

### Post by MajorT on 2006-08-03
Additional 2:
I should also mention that I have in etc/network/options

ip_forward-yes

Regards, Major.

---

### Post by Oxygene on 2006-08-03
Is your server configured to be the default gateway for your "client"-PCs?

Please give us the output of "route -n" on your server and of one of your client-PC's.

---

### Post by MajorT on 2006-08-04
Each PC has the associated router NIC IP as its gateway.
The route -n shows the full list of NICs on the router and the gateway on the PCs.

I did find a solution.

I edited the file /etc/sysctl.conf and un commented the 
net/ipv4/ip_forward=1 line

That did the trick.

Looks like the /etc/network/options file was ignored.

Regards, Major.

---

### Post by Oxygene on 2006-08-04
I think the current state of ip_forward can be read and set in the file /proc/sys/net/ipv4/ip_forward. Maybe the config files are only read when reinitializing the network whil rebooting for example.

So changing the config and doing
```
echo "1" > /proc/sys/net/ipv4/ip_forward
```
should always do the trick.

---

