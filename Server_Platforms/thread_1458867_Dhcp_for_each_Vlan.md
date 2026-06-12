---
title: "Dhcp for each Vlan ?"
date: 2010-04-20
forum: Server Platforms
---

### Post by yesrno on 2010-04-20
Hello,

Recently I was thinking about moving the DHCP task to one of our Linux servers (Ubuntu 9.10 Server edition) but soon I came to a problem. How can I give each VLAN a different ip-range ?
I am using the dhcpd package by the way.
So sure I can let dhcpd send out ip ranges from 172.16.10.x but then how can I make it give out 172.16.20.x to computers on a different vlan ? Because the computers are just connected to the same switch, and they all need to have the same Default gateway.
Was hoping someone with a bit of networking knowledge could help me out here :)

Thanks in advance!

---

### Post by wirelessmonkey on 2010-04-20
You can apply subnet definitions in dhcpd.conf like so:
```

#### Subnet Definitions ####

### 'Vlan-010' Subnet Definition ###
subnet 172.16.10.0 netmask 255.255.255.0 {
     option domain-name-servers 172.16.10.5;
     option routers 172.16.10.1;
     option ip-forwarding off;
}

### 'vlan-20' Subnet Definition ###
subnet 172.16.20.0 netmask 255.255.255.0 {
     option domain-name-servers 172.16.10.5;
     option routers 172.16.10.1;
     option ip-forwarding off;
}

### 'Vlan-030' Subnet Definition ###
subnet 172.16.30.0 netmask 255.255.255.0 {
     option domain-name-servers 172.16.10.5;
     option routers 172.16.10.1;
}


```

My exaple server has a virtual interface on each vlan.

---

### Post by yesrno on 2010-04-20
Yea that would probably work with a 255.255.255.0 mask. But then you're all putting them on different networks right ? If you have 172.16.10.x for 1 vlan and 170.16.11.x for a diffent vlan (with a 255.255.0.0 mask) I receive errors with my dhcp.conf saying its a bad mask. which is kinda logical seeing the subnet ip would be wrong.
Edit: Going to get some sleep now, this is getting me a headache haha. I'll check it again tomorrow, thanks for the help!

---

### Post by Jakob Lundberg on 2010-04-21
Why are you using different vlans if they still have the same default gateway and 172.16.0.0/255.255.0.0 network?

The only way that would work is if the vlans are bridged. And I can't see the point of using different vlans then.

---

### Post by terazen on 2010-04-21
Sounds like you need to check your router config again, because either both ip's are on the same vlan or your subnet mask is wrong.  Or, like Jakob said, you have no need for 2 different vlans in the first place.

Also, you only need 1 ip address on the dhcp server.

---

### Post by Vegan on 2010-04-21
I use hardware networking infrastructure rather than another Linux box to do the same work.

If my needs grow, I get a bigger router. This way I have one box as a firewall, router, gateway and its also DHCP. All the servers and clients are behind this and I then have a topology laid out for the LAN.

Cheap consumer gear can handle at best /255 networks. More expensive stuff can handle larger blocks. How many clients you have determines how much infrastucture you need.

Some servers do not need to be public, others are. This is how you you need to lay out the gear, whether bare metal or virtualized.

---

### Post by bwitherell on 2010-04-22
> **Jakob Lundberg said:**
> Why are you using different vlans if they still have the same default gateway and 172.16.0.0/255.255.0.0 network?

The only way that would work is if the vlans are bridged. And I can't see the point of using different vlans then.

I agree. Having vlans that use the same default gateway does not makes sense. I would even say it is not possible. Even if you bridge them the router/gateway wont route the traffic for the subnets that it is not on. Each subnet/vlan must have its own gateway.

Also, even if you setup the DHCP server correctly there is still no way for the DHCP server to tell which vlan each host is supposed to be on since they are all connected to one switch. You need a router or some other layer 3 device to route between the vlans so the DHCP server can tell which vlan the DHCPREQUEST came from.

Also, why do all the computers need to have the same default gateway?

---

