---
title: "Multiple IP addresses- a variation"
date: 2010-03-03
forum: Server Platforms
---

### Post by cozmos9 on 2010-03-03
I was following a discussion ([http://ubuntuforums.org/showthread.php?t=1358278&page=2](http://ubuntuforums.org/showthread.php?t=1358278&page=2)) and learned much about how things work.  Years ago when I was studying for mcse, never learned much about the underbelly of the network interface configuration.

Anyhow, here's my situation.  I have a system behind a small vlan firewall.  This Ubuntu 9.10 system (let's call this the target) is connected directly to one of 4 configurable ethernet ports on the firewall.  Normally, the port is on the LAN segment, 192.168.1.x.  I have two other segments 192.168.2.x & 3.x.  When I dump large backup image files from vlan2 to to this system on vlan1, I am getting around 550MB/min.  When the source & the target are on the same segment, I've achieved 800-900 MB/min.  So, I am thinking the routing between the segments is slowing things down.

To deal with this, I decided to reassign this target port's vlan membership as needed.  So, working from a vpn connection, I log onto the firewall config page & separately log on to the target system.  I would reboot the target, followed immediately by the port reassignment.

After reading the above thread, I decided to just assign addresses on all 3 subnets and do away with the rebooting.  Just change the vlan port & be done.

The trouble is, if I am on 1.x subnet and need to access resources on 2.x subnet (which used to be very simple with routing rules in the firewall), now the 2.x address wants to handle the packet while connected to the 1.x segment.  At least, that is what I surmise is going on.

Any advices on how to untangle this?  TIA.

---

### Post by KiLaHuRtZ on 2010-03-03
Install the VLAN kernel module and just use a trunk port.  I'd also give your server a dedicated link to the world w/o having to go through the router (this link is also your default route).

Wire it up like this...

```
                           +-----+
   +------(old-nic-eth0)---+ WAN +---+
   |                       +-----+   |
+--+--+                              |
| SRV |                              |
+--+--+                              |
   |                       +-----+   |
   +------(new-nic-eth1)---+ RTR +---+
                           ++-+-++
+----------+                | | |
| VLAN-1.x +----------------+ | |
+----------+                  | |
                              | |
+----------+                  | |
| VLAN-2.x +------------------+ |
+----------+                    |
                                |
+----------+                    |
| VLAN-3.x +--------------------+
+----------+
```

Install and add the 802.1Q kernel module...

```
sudo apt-get install vlan
sudo modprobe 8021q
echo 8021q | sudo tee -a /etc/modules
```

Configure your WAN side interface to use a default gateway...

```
auto eth0 
iface eth0 inet static
address 10.0.0.2
netmask 255.255.255.0
gateway 10.0.0.1
network 10.0.0.0
broadcast 10.0.0.255
```

Setup the VLAN interfaces on your LAN side interface.  Do not set gateways here, the only time it will use this interface is to talk to the respective VLAN.  All other (unknown) traffic will go out the WAN side interface.  I'm assuming your VLAN's are 1,2 & 3.  If not, set up the interface like this 'eth1.[VLAN]'...

```
auto eth1.[COLOR="Red"]1[/COLOR]
iface eth1.[COLOR="Red"]1[/COLOR] inet static
address 192.168.[COLOR="Red"]1[/COLOR].254
netmask 255.255.255.0
network 192.168.[COLOR="Red"]1[/COLOR].0
broadcast 192.168.[COLOR="Red"]1[/COLOR].255

auto eth1.[COLOR="Green"]2[/COLOR]
iface eth1.[COLOR="Green"]2[/COLOR] inet static
address 192.168.[COLOR="Green"]2[/COLOR].254
netmask 255.255.255.0
network 192.168.[COLOR="Green"]2[/COLOR].0
broadcast 192.168.[COLOR="Green"]2[/COLOR].255

auto eth1.[COLOR="Blue"]3[/COLOR]
iface eth1.[COLOR="Blue"]3[/COLOR] inet static
address 192.168.[COLOR="Blue"]3[/COLOR].254
netmask 255.255.255.0
network 192.168.[COLOR="Blue"]3[/COLOR].0
broadcast 192.168.[COLOR="Blue"]3[/COLOR].255
```

You might also like to look at iptables to setup a firewall on the WAN side interface on the server.  And, take a look at fail2ban.  You might also want to run that as well.

Hope this helps!

---

### Post by KiLaHuRtZ on 2010-03-03
Or, you could add a fourth VLAN as the dedicated default route link for your server.  This link would be a /30 network (255.255.255.252) or a 1-to-1.

```
                           +-----+
                           | WAN +---+
                           +-----+   |
+-----+                              |
| SRV |                              |
+--+--+                              |
   |                       +-----+   |
   +------(old-nic-eth0)---+ RTR +---+
                           ++-+-++
+----------+                | | |
| VLAN-1.x +----------------+ | |
+----------+                  | |
                              | |
+----------+                  | |
| VLAN-2.x +------------------+ |
+----------+                    |
                                |
+----------+                    |
| VLAN-3.x +--------------------+
+----------+
```

Configure your interfaces like this...

```
auto eth0.[COLOR="Red"]1[/COLOR]
iface eth0.[COLOR="Red"]1[/COLOR] inet static
address 192.168.[COLOR="Red"]1[/COLOR].254
netmask 255.255.255.0
network 192.168.[COLOR="Red"]1[/COLOR].0
broadcast 192.168.[COLOR="Red"]1[/COLOR].255

auto eth0.[COLOR="Green"]2[/COLOR]
iface eth0.[COLOR="Green"]2[/COLOR] inet static
address 192.168.[COLOR="Green"]2[/COLOR].254
netmask 255.255.255.0
network 192.168.[COLOR="Green"]2[/COLOR].0
broadcast 192.168.[COLOR="Green"]2[/COLOR].255

auto eth0.[COLOR="Blue"]3[/COLOR]
iface eth0.[COLOR="Blue"]3[/COLOR] inet static
address 192.168.[COLOR="Blue"]3[/COLOR].254
netmask 255.255.255.0
network 192.168.[COLOR="Blue"]3[/COLOR].0
broadcast 192.168.[COLOR="Blue"]3[/COLOR].255

auto eth0.[COLOR="Orange"]255[/COLOR]
iface eth0.[COLOR="Orange"]255[/COLOR] inet static
address 192.168.[COLOR="Orange"]255[/COLOR].254
netmask 255.255.255.252
gateway 192.168.[COLOR="Orange"]255[/COLOR].253
network 192.168.[COLOR="Orange"]255[/COLOR].252
broadcast 192.168.[COLOR="Orange"]255[/COLOR].255
```

Make sure to add the gateway address of 192.168.255.253/30 to your router on VLAN 255.

---

### Post by cozmos9 on 2010-03-03
Wow!  Thanks for such a detailed suggestion.  I am going to have to study it a bit...

---

### Post by cozmos9 on 2010-03-04
Ok, KiLaHuRtZ, great suggestion.  I think.  Because I am not fully understanding it.  This may be because my problem is a bit different.  I apologize for not making myself clearer & let me see if I can.

R O U T E R  /  F I R E W A L L
WAN  P1  P2  P3  P4  P5

So, I have a firewall with 6 physical ports.
P1 is LAN 192.168.1.x (downlinks to a 100bt switch)
P2 is VLAN-A 192.168.2.x (downlinks to a wifi AP)
P3 is VLAN-B 192.168.3.x (downlinks to a DMZ switch where public servers are).
P4 is where my workstation connects to.

I want to be able to bind P4 on the fly to any of the segments (P1,2,3) without rebooting the workstation & acquiring a new address, i.e., bridge P4 to P1, P2 or P3 and still have my workstation be able to access any other VLAN and/or WAN.

At this point, this is becoming only a mental exercise to better understand the assignment of multiple ip addresses to a single interface.  This, because I found out the bandwidth cannot be increased by putting the source & the target machines on the same net.  Apparently, the firewall's routing between the VLANs is very fast.

Thanks again.

---

### Post by KiLaHuRtZ on 2010-03-04
In that case, the second option would be better for you.  I thought you had a server needing access to each VLAN.  Just replace "SRV" with your workstation and use option 2 as a guideline.  You don't need to create the 4th VLAN, just set the gateway variable under which ever network/VLAN you want your default route to be.  But do not set a gateway for all three, just one.

Oh, and port 4 would become your trunk port.

---

### Post by cozmos9 on 2010-03-05
Ok.  That last post, I understood.  I am glad to have run into you.  So, tell me this.  What would be the difference between

1. keeping the network segments separate and just allow the firewall to pass the traffic between the segments (which is what I am currently doing).

and

2. trunking the 3 segments on port #4?

Will vlan trunking speed up the data stream across the segments?

---

### Post by KiLaHuRtZ on 2010-03-05
Think of it as this, a VLAN is a logical connection.  Thus, you can have multiple logical connections on one physical connection.  They share the overall bandwith of the physical connection, but that's where it stops.  Trunk ports encapsulate packets and tag them with the VLAN they are a member of.  Access ports strip the tag off and the packet is no loner bound to a VLAN after leaving the port, it's just a normal packet.  So Packet "A" coming from client "1" on access port "1" for VLAN "1" arrives to the router/firewall like this...(using HTML tags to help see this)...

<packet>A</packet>

The router then "tags" it to VLAN 1 because of port 1 being assigned as an access port for VLAN 1.  Once it enters the port, the packet is encapsulated.

<vlan1><packet>A</packet></vlan1>

Lets now assume you have packet "B" coming from client "2" on access port "2" for VLAN "2" and packet "C" coming from client "3" on access port "3" for VLAN "3".

<packet>B</packet> ### Port 2
<packet>C</packet> ### Port 3

The router now tags these, respectively, upon arriving to the port.

<vlan2><packet>B</packet></vlan2>
<vlan3><packet>C</packet></vlan3>

So now the router has three packets, say destined for your workstation.

<vlan1><packet>A</packet></vlan1>
<vlan2><packet>B</packet></vlan2>
<vlan3><packet>C</packet></vlan3>

With the 802.1Q kernel module, your workstation can understand these "tagged" frames.  Whereas, a normal workstation could not understand these packets at all.

You workstation strips off the tags as they enter the respective "sub" interfaces eth0.1, eth0.2 and eth0.3.  Mind you, only packets with a tag for vlan 1 will go and come from eth0.1 and packet for vlan 2 will only go and come from eth0.2, and so forth.  The only way a packet could "jump" VLANs is if you setup static routes on your workstation which would technically turn it into a router.

So in short, you networks are still isolated and visual it like your workstation has three physical connections, one to each network.  But in reality, it has one physical connection with three logical connections inside of it.  Think of it like an Ethernet cable, you have one physical cable, but 8 wires inside.  Can the electrons jump wires or see each other on they way to there destination?  No.  Trunk ports work like that.

On the inverse, when a packet leaves your workstation on eth0.2 for client "2" for VLAN "2".  Your workstation tags the packet/frame like stated above.  The router then understands this and know client "2" is on port "2" because of the MAC table entry.  So the packet arrives at port "2" and the router strips the "tag" of ans sends a normal packet out on the wire so the client can read said packet.

I hope that answers a good deal of your questions.  Google "router on a stick" when you have some time.

Also, one other thing to note.  All that was said above is all layer 2.  When a client on VLAN 1 wants to talk to a client on VLAN 2.  The router will go up to layer 3 and "route" the packets between network segments.  Thus, packet comes in on port 1, gets a tag for vlan 1.  goes to the gateway address, say x.x.1.1.  Its now a layer 3 packet, gets punted to the router processor.  The route processor examines the packet and sees it is destined for x.x.2.y.  It looks up that network in the routing table and find it has a route to it on vlan2.  So it sends it the the vlan2 interface where the packet recieves a vlan-2 tag.  It gets sent to acces port 2 where the tag is removed and then gets sent on its merry way to the other client.

Oh, and did I mention I'm a network engineer for a living? ;) ;) ;)

---

### Post by KiLaHuRtZ on 2010-03-05
> **cozmos9 said:**
> 1. keeping the network segments separate and just allow the firewall to pass the traffic between the segments (which is what I am currently doing).

This is still in place.

> **cozmos9 said:**
> 2. trunking the 3 segments on port #4?

Your workstation is not a router, so there is no traffic crossing VLAN's here.  They only route between segments via layer 3 on your router/firewall as you stated in you first question.

> **cozmos9 said:**
> Will vlan trunking speed up the data stream across the segments?

You are already tagging frames internally on the router.  Just all your packets are untagged when on the wire.  You may see a slight speed increase seeing as the router will no longer have to tag/untag frames on port 4.  It sends them out to the workstation unmodifed and your workstation will now do the tagging/untagging for port 4 (theoretically).

Again, look at "router on a stick".  This is basically what you are doing, but your only modification is a workstation hanging off the router with the ability to process tagged frames and listen on multiple VLANs and an egress WAN link to the world.

---

### Post by KiLaHuRtZ on 2010-03-05
Whoever made this, I credit them, for I stole it off Google images to explain my case...

[IMG]http://www.dankrusi.com/HistoryofNetworking2_6670747065794371787030786D853B867975867B51494B473E867B9349858388878996605755564DA08D8C589A8E9B946D8193999775A1A0A697A0A6A558AA96945F989B9E976F7A9BA5A6A1A4ABA1988097A6A9A1A49D9BA09964609CA299.jpg[/IMG]

Look at the core layer (3).  "Central Server" is like your workstation.  The router and the switch are combined into one unit that is your router/firewall.

---

### Post by cozmos9 on 2010-03-05
Totally clear.  I understand now that using your suggestion, my workstation is not bridging the segments and keeps them separate as far as the rest of the network is concerned.  I guess I just have to harden the workstation against a breach.  Much appreciated.  BTW, I did wonder if you were a cisco type engineer.  Shows you know your stuff.

---

### Post by KiLaHuRtZ on 2010-03-05
> **cozmos9 said:**
> BTW, I did wonder if you were a cisco type engineer.  Shows you know your stuff.

No, but I do have a few Cisco certifications. :D

---

