---
title: "Problem with multiple NIC's on server"
date: 2013-01-04
forum: Server Platforms
---

### Post by knutz on 2013-01-04
Hi guys!


I'm in a bit of a pickle here and I really hope you can help me.
I'm running Ubuntu Server 11.10 on a server with 4 Ethernet ports.

I've configured two static IP addresses on two different Ethernet ports. 

My **/etc/network/interfaces** looks like this:
```

auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet static
	address 192.168.113.18
	netmask 255.255.255.0
	broadcast 192.168.113.255
	network 192.168.113.0
	gateway 192.168.113.254

iface eth1 inet static
	address 192.168.113.19
	netmask 255.255.255.0
	broadcast 192.168.113.255
	network 192.168.113.0

```

Now, my problem is kind of weird. 
When I ping 192.168.113.18 I get a response. When I ping 192.168.113.19 I get a response.
[LIST=1]
[*]If I pull the Ethernet-cable out of eth0 while eth1 still being connected, both .18 and .19 is unresponsive. 
[*]If I pull the Ethernet-cable out of eth1 while eth0 still being connected, I still get a response from both .18 and .19.
[/LIST]

What can this be?

*The attached interfaces.txt file is the original interfaces file. I stripped it down to only eth0 and eth1 for testing this weird behaviour.

---

### Post by NigelRen on 2013-01-04
What do you get when you run 'route'.   I think you'll find that eth0 is acting as a gateway for anything 192.168.113.*  So if eth0 is down it won't be able to do anything - as you've found.

---

### Post by dannyboy79 on 2013-01-04
in order to help I think we need to know what you're trying to accomplish with all 4 of these NICs

---

### Post by knutz on 2013-01-04
> **NigelRen said:**
> What do you get when you run 'route'.   I think you'll find that eth0 is acting as a gateway for anything 192.168.113.*  So if eth0 is down it won't be able to do anything - as you've found.

The output of route is:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.113.254 0.0.0.0         UG    100    0        0 eth0
192.168.113.0   *               255.255.255.0   U     0      0        0 eth0
192.168.113.0   *               255.255.255.0   U     0      0        0 eth1

```

---

### Post by knutz on 2013-01-04
> **dannyboy79 said:**
> in order to help I think we need to know what you're trying to accomplish with all 4 of these NICs

Well. I want eth0 to have the address 192.168.113.18 and eth1 to have the address 192.168.113.19. 
As it is now, both IP addresses is on the NIC eth0.

---

### Post by dannyboy79 on 2013-01-04
why would you want the same computer to have 2 IP's from the same subnet? just curious, trying to understand your end goal

---

### Post by knutz on 2013-01-05
> **dannyboy79 said:**
> why would you want the same computer to have 2 IP's from the same subnet? just curious, trying to understand your end goal

In the original setup:
Well, the Server serves as a multi-user VirtualBox environment. All the users have a VirtualBox instance. Each of these users have a tap interface which is bridged to eth2. The virtual machines serves as workstations for each user.
eth1 serves all the virtual servers.
All traffic through eth0 is the RDP connections to each workstation and the VirtualBox webserver.

In the test setup:
So, I want all the RDP connection- and web-traffic on one NIC and all the Virtual Machine traffic on another. Even though they are on the same network.

---

### Post by dannyboy79 on 2013-01-05
ok, wow, this is way over my head. sorry can't help. lol

---

### Post by NigelRen on 2013-01-05
> **knutz said:**
> The output of route is:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.113.254 0.0.0.0         UG    100    0        0 eth0
192.168.113.0   *               255.255.255.0   U     0      0        0 eth0
192.168.113.0   *               255.255.255.0   U     0      0        0 eth1

```

Which is what I was saying - eth0 is your main route out.

OK - so what are you trying to achieve by unplugging the cables?  Is this just curiosity or are you trying to achieve something with it?

---

### Post by spynappels on 2013-01-05
> **knutz said:**
> In the original setup:
Well, the Server serves as a multi-user VirtualBox environment. All the users have a VirtualBox instance. Each of these users have a tap interface which is bridged to eth2. The virtual machines serves as workstations for each user.
eth1 serves all the virtual servers.
All traffic through eth0 is the RDP connections to each workstation and the VirtualBox webserver.

In the test setup:
So, I want all the RDP connection- and web-traffic on one NIC and all the Virtual Machine traffic on another. Even though they are on the same network.

Could you explain the reasoning behind this a little further? Is it because of bandwidth reasons on each interface? If it is, another solution would be to use Link Aggregation to bond several interfaces into one bonded interface capable of greater bandwidth. It does require a LA capable switch, but most enterprise switches are.

---

### Post by darkod on 2013-01-05
> **spynappels said:**
> Could you explain the reasoning behind this a little further? Is it because of bandwidth reasons on each interface? If it is, another solution would be to use Link Aggregation to bond several interfaces into one bonded interface capable of greater bandwidth. It does require a LA capable switch, but most enterprise switches are.

There are many synonims, but the so called static bonding doesn't require a switch that supports the dynamic LACP protocol. It will simply be bunch of ports acting as one.

I agree that if this is for bandwith, bonding is the way to do it. Otherwise it makes no sense having IPs from the same subnet on two ports.
[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

PS EDIT: To complement my post, it would still require a switch that support static LA but even ancient switches support this, even the ones not supporting LACP.

---

### Post by knutz on 2013-01-05
> **NigelRen said:**
> Which is what I was saying - eth0 is your main route out.

OK - so what are you trying to achieve by unplugging the cables?  Is this just curiosity or are you trying to achieve something with it?

No, I wasn't trying to achieve anything. It was by pure coincidence that I discovered that both addresses where unresponsive when I unplugged one cable.

---

### Post by knutz on 2013-01-05
> **darkod said:**
> There are many synonims, but the so called static bonding doesn't require a switch that supports the dynamic LACP protocol. It will simply be bunch of ports acting as one.

I agree that if this is for bandwith, bonding is the way to do it. Otherwise it makes no sense having IPs from the same subnet on two ports.
[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

PS EDIT: To complement my post, it would still require a switch that support static LA but even ancient switches support this, even the ones not supporting LACP.


Well to answer both spynappels' and darkod's replies:

Yes the reason is actually bandwith. :) So bonding seems to be the way to go. 
But can you bridge TAP interfaces to a bonding interface?

---

### Post by spynappels on 2013-01-05
> **knutz said:**
> Well to answer both spynappels' and darkod's replies:

Yes the reason is actually bandwith. :) So bonding seems to be the way to go. 
But can you bridge TAP interfaces to a bonding interface?

You should be able to, the bonded interface will be something like bond0 and can be used in exactly the same way as eth0 or eth1 would be.

Another advantage is that it only uses 1 IP instead of 2, less wasteful...

---

### Post by knutz on 2013-01-05
> **spynappels said:**
> You should be able to, the bonded interface will be something like bond0 and can be used in exactly the same way as eth0 or eth1 would be.

Another advantage is that it only uses 1 IP instead of 2, less wasteful...

Okay, thank you very much all! 
I'll try this first thing monday morning.
Have a great weekend. :)

---

