---
title: "Openvpn Site-to-Site: impossibile to ping client on subnet"
date: 2010-06-25
forum: Server Platforms
---

### Post by Debie on 2010-06-25
Hi all,
I have to ubuntu machine (9.10 and 10.4) with a openvpn tunnel between them.
This is the situation:

```

NetworkA 192.168.0.0/24
|
UbuntuA br0:192.168.0.3 (openvpn bridge between eth0 and tap0)
|
Internet
|
UbuntuB internet interface eth0:192.168.150.2, inernal lan interface eth1:192.168.2.1
|
NetworkB 192.168.2.0/24

```UbuntuA has one only interface etho and there are two openvpn instance: one bridge istance with br0 and another instance with tun0.
UbuntuA is not the gateway for networkA. UbuntuB is the gateway for NetworkB.

I need to comunicate between pc on networkB e those on networkA.
This is the "ping situation" (no pc tested has an active firewall):


[LIST]
[*]ubuntuA vs  ubuntuB: OK
[*]ubuntuB vs  ubuntuA: OK
[*]pc on NetworkA vs ubuntuA and ubuntuB: OK
[*]pc on NetworkA vs ubuntuA and ubuntuB: OK
[*]ubuntuA vs pc on NetworkB: OK
[*]pc on NetworkB vs pc on NetworkA: NO (this is i really need)
[/LIST]

All this ping are checked vs the UbuntuA and UbuntuB with theri openvpn IP (10.0.2.1 and 10.0.2.2)
If I try to ping UbuntuA and UbuntuB using their internal ip address this is what i get:


[LIST]
[*]ubuntuB vs UbuntuA (internal IP address 192.168.0.3): OK
[*]ubuntuA vs UbuntuB (internal IP address 192.168.2.1): OK
[*]pc on NetowrkB vs UbuntuA (internal IP address 192.168.0.3): OK
[/LIST]

This is the route -n on both ubuntu machine:

**ubuntu A**

```

Codice:
Destination     Gateway         Genmask         Flags Metric Ref    Use  Iface
10.0.2.2        0.0.0.0         255.255.255.255 UH    0      0        0  tun0
192.168.2.0     10.0.1.1        255.255.255.0   UG    0      0        0  tun0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0  br0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0  br0

```
**ubuntuB**

```

Codice:
Destination     Gateway         Genmask         Flags Metric Ref    Use  Iface
10.0.2.1        0.0.0.0         255.255.255.255 UH    0      0        0  tun0
192.168.2.0     0.0.0.0        255.255.255.0   UG    0      0        0  eth1
192.168.150.0     0.0.0.0         255.255.255.0   U     0      0        0  eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0  tun0
0.0.0.0         192.168.150.1     0.0.0.0         UG    100    0        0  eth0

```What's going wrong?

---

### Post by koenn on 2010-06-25
there's info missing.
You probably have most of the pieces in place, but you also need to have a look at (or post here) the routing table on the PC's (not just the servers)

Net B is probably OK as it uses ServerB as default gateway, and server B knows a route to NetworkA

PCs on NetworkA also need to have a route to NetworkB, or a default gateway that knows such a route.

---

### Post by Debie on 2010-06-25
Thank you for the replay.
I attach an image of the routing table of one of the pc on NetworkA i need to reach from networkB.
I've added the route 192.168.2.0  255.255.255.0 192.168.0.3 and deleted the route 192.168.2.5 ....
Everytime i try to ping from this pc one of the pc on networkB i foung again the route 192.168.2.5 .... in the routing table
Anyway also with route 192.168.2.0  255.255.255.0 192.168.0.3 i can't ping this pc from networkB.


[IMG]http://img444.imageshack.us/img444/5783/routingtable.jpg[/IMG]

---

### Post by koenn on 2010-06-25
I don't understand why you think a route to 192.168.2.0 is going to help. That network doesn't even occur in your description.

Anyway,
the routing table on that PC goes to 192.168.0.1 for almost everyting (default), while your tunnel starts on 192.168.0.3
that PC (and all others on network A) need a route to 192.168.1.0/24 via 192.168.0.3, or
192.168.0.0/24's default gateway 192.168.0.1 needs a route to 192.168.1.0/24 via 192.168.0.3

that way, the replies to your ping know how to get back to the pc that requested them.

---

### Post by Debie on 2010-06-26
> **koenn said:**
> I don't understand why you think a route to 192.168.2.0 is going to help. That network doesn't even occur in your description.

Anyway,
the routing table on that PC goes to 192.168.0.1 for almost everyting (default), while your tunnel starts on 192.168.0.3
that PC (and all others on network A) need a route to 192.168.1.0/24 via 192.168.0.3, or
192.168.0.0/24's default gateway 192.168.0.1 needs a route to 192.168.1.0/24 via 192.168.0.3

that way, the replies to your ping know how to get back to the pc that requested them.

I'm sorry for the mistake. I've updated the first post.
NetwokA is on the 192.168.0.0 subnet, the networkB is on the 192.168.2.0 subnet.
This is why I added the route 192.168.2.0 255.255.255.0 192.168.0.3.


P.S.: 192.168.1.0 is a third network managed by a router cisco (192.168.0.1).
P.P.S.: 192.168.0.3 is a ubuntu machine with a nat 1-to-1 performed by the router cisco and it has a static ip address.

---

### Post by koenn on 2010-06-26
> **Debie said:**
> I'm sorry for the mistake. I've updated the first post.
NetwokA is on the 192.168.0.0 subnet, the networkB is on the 192.168.2.0 subnet.
This is why I added the route 192.168.2.0 255.255.255.0 192.168.0.3.


P.S.: 192.168.1.0 is a third network managed by a router cisco (192.168.0.1).
P.P.S.: 192.168.0.3 is a ubuntu machine with a nat 1-to-1 performed by the router cisco and it has a static ip address.

it's getting messier and messier. Now you also have a cisco router in there, and something (the router ? UbuntuA server?) is doing NAT ?

Maybe you should draw/describe your network again with those included 
 Where is that cisco router ? What is your NAT doing exactly ? If you have  NAT, does that mean you are using IPtables ? And if so, do you have any filtering going on as well ? 

Looks like you're going to have to test every segment separately to pinpoint the problem.

And just to make sure : do you have ip forwarding enabled on both ubuntu servers ?

edit: another inconsistency;
who is 10.0.[COLOR="Red"]**1**[/COLOR].1 in
```
192.168.2.0     10.0.1.1        255.255.255.0   UG    0      0        0  tun0
```
your tunnel is apparently 10.0.**2**.1-10.0.**2**.2

---

### Post by koenn on 2010-06-26
and just to check:
does it work if you set the default gw on the network A pcs to 192.168.0.3 ?

---

