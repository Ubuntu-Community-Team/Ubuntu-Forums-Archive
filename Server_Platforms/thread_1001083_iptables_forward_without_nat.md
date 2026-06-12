---
title: "iptables forward without nat?"
date: 2008-12-03
forum: Server Platforms
---

### Post by xyrer on 2008-12-03
Hi, I've been trying to forward some traffic going to a certain ip so it goes to another one, the problem comes with the nat, i need the packets to stay just the way they were sent, this is the scenario:
pc1 tries to connect to 10.10.57.4, the server has to redirect that connection to 10.10.2.20 which is a lan2lan device that catches the request to the 57.4 and sends it to the real pc that has the .57.4 ip on another building.
So far I have tried prerouting the packages but they get stuck at the .2.20 device, when I ping it's only the device the one who answers, it doesn't transport the ping to the real machine.

I hope I made myself clear, only thing to say is that the lan2lan device is not removable, it has to be there, the only thing I want to remove is a cisco router which only does the routing for that and it's expensive so it would be very good to get it out of there.

I appreciate any guidance.

---

### Post by cdenley on 2008-12-03
So where are the "server" and "lan2lan device" on your network. Are they both on the same switched network? How would traffic sent to 10.10.57.4 end up going to the "server" so it can be redirected? Is the "server" some sort of router or bridge? What sort of traffic are you trying to forward? A particular TCP port?

---

### Post by xyrer on 2008-12-04
Yes, they are on the same switch and same subnet, server has the .2.1 and the lan2lan has the .2.20.
I did preroute pings and they did very good, but lan2lan is not supposed to answer so it's a not complete solution, I suppose I have to work with the "route" command instead of iptables but I've never used that and can't find a good example on google.
the server is the gateway, broadcasted via dhcp to all the other pcs, the server is a hp proliant ml110 with ubuntu server 7.04 and I want all udp traffic sent to any .57.0 ip to be redirected to the lan2lan device, and of course, I suppose the way back should work just fine.

i hope I made myself clear. Thanks.

---

### Post by cdenley on 2008-12-04
So you want traffic coming to the gateway to be redirected to 10.10.2.20, which already is configured to send incoming traffic to the appropriate server on the other lan?

```

sudo iptables -t nat -I PREROUTING -p udp -d 10.10.57.0/24 -j DNAT --to-destination 10.10.2.20

```

---

### Post by xyrer on 2008-12-04
yes, I tried that already, but the nat (network address translation) makes the lan2lan device to receive the data as if it comes from the server, the second problem is that the request header changes and it now points to 10.10.2.20 and not 10.10.57.x, so the lan2lan answers itself and it doesn't transfer the request to the real 10.10.57.x at the other side.

---

### Post by cdenley on 2008-12-04
I believe that would require the "ROUTE" target which does not seem to be included in ubuntu.
[http://www.netfilter.org/documentation/HOWTO/netfilter-extensions-HOWTO-4.html#ss4.5](http://www.netfilter.org/documentation/HOWTO/netfilter-extensions-HOWTO-4.html#ss4.5)

---

### Post by koenn on 2008-12-04
If you need to make packets jump through hoops like that, you probably have a design problem at the network level. 

From what I understand from your posts (there seems to be some info missing ...)  it should be sufficient to either

A/ use the LAN2LAN device as the default gateway for pc1 etc. Assuming that device is also connected to the 10.10.57.0 network, it will route your packets straight to their destination.
That thing you call server is standing in the way; there's no (apparent) reason a packet with destination 10.10.57.x should pass through a machine that doesn't know how to forward them to the destination network.

or B/ 
tell the 'server' that any packet with destination on 10.10.57.0/mask needs to be handed over to that lan2lan thing, assuming that device will know what to do with it. Something like
```
route add -net 10.10.57.0 netmask 255.255.255.0 gw 10.10.2.2
```

---

### Post by xyrer on 2008-12-04
As a matter of fact, the B might be just what I need, the lan2lan can't be gateway because of the lack of internet, I need proxy and stuff.
So that command... is there any pre-requisite for that to work? I mean, it looks like the server needs to have an interface configured to that subnet or something, I will study it anyway, but to be clear... does that command means that everything going to 10.10.57.0 is going to 10.10.2.2 regardless of where that ip is?

---

### Post by koenn on 2008-12-05
> **xyrer said:**
> the lan2lan can't be gateway because of the lack of internet, I need proxy and stuff.
it probably can if it has a default route out to the internet. And if you have web access through a proxy, that proxy needs some way of internet access, but that doesn't necessarily mean the proxy itself needs to be on a router that is configured to be default gateway for the hosts that use the proxy. 
And so on. Your network as a whole might need some work, but for now option B/ might be the easiest / preferred approach

> **xyrer said:**
> 
So that command... is there any pre-requisite for that to work? I mean, it looks like the server needs to have an interface configured to that subnet or something, I will study it anyway, but to be clear... does that command means that everything going to 10.10.57.0 is going to 10.10.2.2 regardless of where that ip is?
pre-requisite : the server needs a way to communicate with 10.10.2.20, but as they are on the same subnet, that's covered. 
The added route will probably disappear when you reboot, because it's not discoverable. You can use a startup script to set it at every system restart, same as you do with iptables statements. 

what it does: it creates an entry in the kernel routing table, saying that any packet with a destination address that is in subnet 10.10.57.0/255.255.255.0 should be send to 10.10.2.20 ; no more, no less.

10.10.2.20 will re-evaluate the packet's destination, and take the next routing decision - if 10.10.2.20 knows a route to 10.10.57.0/255.255.255.0, the packet will be sent on that route. If not, it will be sent on 10.10.2.20's default route.

I have no 2 spare networks handy to test it all, but I'm pretty sure it'll work. Maybe the route command needs some tweaking (man route for syntax etc). You might have to check the routing on that lan2lan thingie to make sure reply-packets can be routed back from 10.10.57.0/255.255.255.0 to where-ever the need to go.

---

### Post by xyrer on 2008-12-06
That made it way clear, I'll check it out.
Thanks a lot.

---

### Post by xyrer on 2009-01-28
Ok, took a long while but I got it working just like you said, it worked like a charm.
Thanks a lot.

---

### Post by koenn on 2009-01-29
great.

---

