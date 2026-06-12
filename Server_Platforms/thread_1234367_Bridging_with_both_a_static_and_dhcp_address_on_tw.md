---
title: "Bridging with both a static and dhcp address on two NICs"
date: 2009-08-07
forum: Server Platforms
---

### Post by Gen2ly on 2009-08-07
Hello guys.  I'm trying to build a router with snort inline.  For it to work I need to bridge my two NIC's.  The WAN nic will be dhcp and the LAN nic will be static.  So far I've come up with this:

```
auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
bridge_ports eth0 eth1

auto eth1
iface eth1 inet static
address 192.168.43.100
netmask 255.255.255.0
broadcast 192.168.43.255
gateway 192.168.43.1
```

This will connect to the internet, and assign eth1 the ip of 192.168.43.100.  Problem is, if I try to connect the lan computer to the router it fails to connect.  A basic /etc/network/interfaces works though if I 'rmmod bridge' and reconfigure the interfaces:

```
auto lo
iface lo inet loopback

iface eth1 inet static
address 192.168.43.100
netmask 255.255.255.0
broadcast 192.168.43.255
gateway 192.168.43.1
```

and try to connect.

Why am I having trouble connecting to the static-nic?

---

### Post by DGortze380 on 2009-08-07
please post the output of 

```

route

```

---

### Post by Gen2ly on 2009-08-07
Oy! Should've thought of that:

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.43.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
24.181.42.0     0.0.0.0         255.255.254.0   U     0      0        0 br0
0.0.0.0         192.168.43.1    0.0.0.0         UG    0      0        0 eth1
0.0.0.0         24.181.42.1     0.0.0.0         UG    0      0        0 br0
```

Looks alright?  I've never seen Genmask of 255.255.254.0 before.

---

### Post by Gen2ly on 2009-08-08
Am I able to set up a bridge like this?  From the examples I've seen no ip address is set for the LAN nic, for example:

```
 auto lo
      iface lo inet loopback 

 auto br0
 iface br0 inet static
      address 192.168.1.22
      netmask 255.255.255.0
      broadcast 192.168.1.255
      gateway 192.168.1.1
    # Ports you want to add to your bridge
    bridge_ports eth0 eth1
    # Time to wait before loading the bridge
    bridge_maxwait 0 
```

Is it possible I'm trying to do the impossible and need another nic?

---

### Post by DGortze380 on 2009-08-08
> **Gen2ly said:**
> Oy! Should've thought of that:

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.43.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
24.181.42.0     0.0.0.0         255.255.254.0   U     0      0        0 br0
0.0.0.0         192.168.43.1    0.0.0.0         UG    0      0        0 eth1
0.0.0.0         24.181.42.1     0.0.0.0         UG    0      0        0 br0
```

Looks alright?  I've never seen Genmask of 255.255.254.0 before.

Honestly, I don't know that much about bridging...

but I do see a problem with your routing table. You essentially have two default routes.

The second to last route says "For all IP addresses that are not 192.168.43.x(this subnet is handled by your first rule) use the gateway at 192.168.43.1 through interface eth0"

That's ok.

But the next rule says "For all IP addresses that are not 24.181.[0-1].x (again, handled by the second rule) uset he gateway at 24.181.42.1 through interface br0"

So you can see that becomes a problem. They conflict.

Do you have a link to the documentation you used to set up the bridge. I have a feeling something isn't right here, but I'd have to do some research to track it down. Not enough experience with bridges.

Also the output of ifconfig while your bridge is 'running'.

---

### Post by Gen2ly on 2009-08-08
Thanks for the great reply DGortze380.  Haven't been much about routing but I see what you mean.

As for the bridge, I looked at the page again that bridged both dhcp and static and I think it's bunk.  Looked at several pages since and I do think I have misunderstood the concept of bridging.  Basically put: bridging connects two interfaces to act as one (e.g. connecting a wifi nic and wired nic together to be filtered in a firewall together.  I'm pretty sure at this point I'm trying to do an impossible bridge.

---

### Post by Vegan on 2009-08-08
Bridging was not really meant for what you are trying to do.

You should be using ALL static addresses for you to be sucessful. As for firewalls etc, a bridge is not a firewall.

Orginally it was intended to link disparate local area networks. For example a research center that is remote from the data sources.

You will need a lot of hardware to make a real bridge. 2 NICs is only part of the bigger problem.

---

### Post by DGortze380 on 2009-08-08
> **Gen2ly said:**
> Thanks for the great reply DGortze380.  Haven't been much about routing but I see what you mean.

As for the bridge, I looked at the page again that bridged both dhcp and static and I think it's bunk.  Looked at several pages since and I do think I have misunderstood the concept of bridging.  Basically put: bridging connects to interfaces to act as one (e.g. connecting a wifi nic and wired nic together to be filtered in a firewall together.  I'm pretty sure at this point I'm trying to do an impossible bridge.

You're overall goal I think is definitely doable. There are a number of tools to turn a linux box into a fully functioning router. And running a snort sensor on the same box is certainly feasible. I think you should probably start from scratch though. Sounds like you're started in the direction.

Take it one step at a time, get the router up and going. Be sure to post any specific questions in appropriate threads and I think you can get it going.

Good Luck!

---

### Post by aesis05401 on 2009-08-09
Hey, 

You should be defining the nics as if they were totally independent of each other.  Then use iptables/NetFilter to forward and transform packets.    

Iptables entry material courtesy of bohdi.zazen:[http://bodhizazen.net/Tutorials/iptables/]("http://bodhizazen.net/Tutorials/iptables/")

Good starting guide to firewall configuration through a  script (this includes a handy ip transformation rule you should be using when packets are crossing from the LAN to the WAN):[http://www.novell.com/coolsolutions/feature/18139.html]("http://www.novell.com/coolsolutions/feature/18139.html")

Does this help?

---

### Post by Gen2ly on 2009-08-09
Having to build Debian/Ubuntu, does mean a few things from the get go,  starting from scratch... maybe not a bad idea.  In fact, I think it's a very good idea. :)  I got my Debian router pretty well built, but learning a good bit still about networking.  Building a computer: that's easy, getting a good firewall up... that's an art.

---

### Post by Gen2ly on 2009-08-09
> **aesis05401 said:**
> Hey, 

You should be defining the nics as if they were totally independent of each other.  Then use iptables/NetFilter to forward and transform packets.    

Iptables entry material courtesy of bohdi.zazen:[http://bodhizazen.net/Tutorials/iptables/]("http://bodhizazen.net/Tutorials/iptables/")

Good starting guide to firewall configuration through a  script (this includes a handy ip transformation rule you should be using when packets are crossing from the LAN to the WAN):[http://www.novell.com/coolsolutions/feature/18139.html]("http://www.novell.com/coolsolutions/feature/18139.html")

Does this help?

Yeah, I'm building snort in inline-mode which requires bridging two nic's to queue packets for drop ability by snort.  I thought I could extend the bridge to both a LAN and WAN address, but...  For iptables, yeah, I'm going have to do routing... err forwarding and figure out how I will do that with another nic.  Bodhi's tutorial is actually very good.  Thanks for the link.

---

### Post by aesis05401 on 2009-08-09
> **Gen2ly said:**
> Yeah, I'm building snort in inline-mode which requires bridging two nic's to queue packets for drop ability by snort.  I thought I could extend the bridge to both a LAN and WAN address, but...  For iptables, yeah, I'm going have to do routing... err forwarding and figure out how I will do that with another nic.  Bodhi's tutorial is actually very good.  Thanks for the link.

I have never used snort in this manner.  I am currently following instructions in [*_Linux Firewalls_*]("http://books.google.com/books?id=fOM-AAAACAAJ&dq=Linux+Firewalls+Rash&lr=") by Michael Rash to transform snort rules through fwsnort into iptables rules so that snort does not need to be run inline.

The theory is that iptables rules designed to emulate snort inspection results in a faster stack, but I don't know what the trade-offs are yet, I'm still a n00b to packet inspection techniques.

---

