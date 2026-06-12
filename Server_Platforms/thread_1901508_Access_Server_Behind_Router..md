---
title: "Access Server Behind Router."
date: 2011-12-28
forum: Server Platforms
---

### Post by KoolAidJunkie on 2011-12-28
I currently have an Ubuntu Server running behind a Router (#2), which is also attached to another Router/Modem(#1). If I am connected to Router #2 I can access the server just fine, but can not see or communicate with the Server in any way when connected to router #1.

The routers are not bridge in anyways, they are running as normal. Router #2 is connected to Router #1 via Ethernet (cat5) - the end located at Router #1 is plugged into one of the 4 Etherports, while the end of the cat5 cable is pluggin into the WAN port.

On Router #1 I set a static Internal IP (198.168.XXX.XXX) for Router #2, and on Router #2 I set up the WAN settings to match that Internal IP and DNS information from Router #1.

Router #2 can access the internet just fine, no issues what so ever. So as far as I know the issue does not come from the Router set up...

How would I access the server when connected to Router #1?

---

### Post by collisionystm on 2011-12-28
> **KoolAidJunkie said:**
> I currently have an Ubuntu Server running behind a Router (#2), which is also attached to another Router/Modem(#1). If I am connected to Router #2 I can access the server just fine, but can not see or communicate with the Server in any way when connected to router #1.

The routers are not bridge in anyways, they are running as normal. Router #2 is connected to Router #1 via Ethernet (cat5) - the end located at Router #1 is plugged into one of the 4 Etherports, while the end of the cat5 cable is pluggin into the WAN port.

On Router #1 I set a static Internal IP (198.168.XXX.XXX) for Router #2, and on Router #2 I set up the WAN settings to match that Internal IP and DNS information from Router #1.

Router #2 can access the internet just fine, no issues what so ever. So as far as I know the issue does not come from the Router set up...

How would I access the server when connected to Router #1?

Modem/router, lan port, 192.168. address
ROUTER2, wan port, wan points to router 1
 Ubuntu

Okay first things first.
Why do you have 2 routers?

Lets assume 'router 1' is just given to you from the provider.
I will also assume you may have 'router 2' to provide wireless?

The fact of the matter is, with this setup, it should be as follows. ( i am guessing alot until you tell more )
If i go with my assumptions

Router 1 should provide DHCP to the local network and interface with the internet
Router 2 should be connected via 1 of its 4 lan ports to router 1 via 1 of its 4 lan ports. No WAN on router 2.

Router 2 should just exist on your network as a node, and should not be trying to route anything. 

all your routing should happen in router 1. 

If you can provide more information... I can help more.

---

### Post by KoolAidJunkie on 2011-12-28
> **collisionystm said:**
> Modem/router, lan port, 192.168. address
ROUTER2, wan port, wan points to router 1
 Ubuntu

Okay first things first.
Why do you have 2 routers?

Lets assume 'router 1' is just given to you from the provider.
I will also assume you may have 'router 2' to provide wireless?

The fact of the matter is, with this setup, it should be as follows. ( i am guessing alot until you tell more )
If i go with my assumptions

Router 1 should provide DHCP to the local network and interface with the internet
Router 2 should be connected via 1 of its 4 lan ports to router 1 via 1 of its 4 lan ports. No WAN on router 2.

Router 2 should just exist on your network as a node, and should not be trying to route anything. 

all your routing should happen in router 1. 

If you can provide more information... I can help more.

Router #1 = Cateway IP 192.168.0.1, External IP assigned by ISP
Router #2 = Gateway IP 192.168.1.1, IP set by Router #1 192.168.0.111

I have two routers for 2 different Wifi Access points.
Both routers provided DHCP. I guess I could set the 2 router as a simple etherswitch (bridge) but connect via the Etherports instead of the WAN port.

This place is a Duplex, my cousin lives down stairs, and I upstairs. I ran cat5 cable from his router to mine. The 2nd router is set up the way it is so that I can control the computer connect to the wifi in my place. He refuses to use any Wireless encryption other than WEP, and I prefer WPA2. The 2nd router allows me to control the access times of my kids computer. So that is why there are 2 routers
Plus AT&T refused to install a second DSL line, unless I upgrade to a Business line. So I just share the cost with my cousin on the 1.

The Server is connect to my router (#2) and I was trying to allow cousin access the the Media Share (Movies/Music) - If I open up the network (ie disable DHCP on router #2 and set to bridge) than allows him access to the network between my Work PC, Laptop, and my Kids computer. Was trying to avoid that.

---

### Post by rubylaser on 2011-12-29
> **KoolAidJunkie said:**
> Router #1 = Cateway IP 192.168.0.1, External IP assigned by ISP
Router #2 = Gateway IP 192.168.1.1, IP set by Router #1 192.168.0.111

I have two routers for 2 different Wifi Access points.
Both routers provided DHCP. I guess I could set the 2 router as a simple etherswitch (bridge) but connect via the Etherports instead of the WAN port.

This place is a Duplex, my cousin lives down stairs, and I upstairs. I ran cat5 cable from his router to mine. The 2nd router is set up the way it is so that I can control the computer connect to the wifi in my place. He refuses to use any Wireless encryption other than WEP, and I prefer WPA2. The 2nd router allows me to control the access times of my kids computer. So that is why there are 2 routers
Plus AT&T refused to install a second DSL line, unless I upgrade to a Business line. So I just share the cost with my cousin on the 1.

The Server is connect to my router (#2) and I was trying to allow cousin access the the Media Share (Movies/Music) - If I open up the network (ie disable DHCP on router #2 and set to bridge) than allows him access to the network between my Work PC, Laptop, and my Kids computer. Was trying to avoid that.

As collisionystm said, you really only need/want to have 1 router on your network.  turn off the DHCP server on the second router and connect router 1 into router 2 by the LAN ports on the back rather than the WAN port.  This will make the second router act like a switch and a wireless access point (you'll want to give router 2 a static ip in the same subnet as router 1 as well).

This will put all of your devices in the same subnet (192.168.0.0/24) and will make your life much easier.  As it is, for your cousin to see your server, you'd need to either setup a VPN connection for him to connect to your network, or do port forwarding for all the necessary ports for the services you're trying to provide.  I'd just tell your cousin if he wants access to your media, you want him to run WPA2 encryption on this wireless router. Otherwise leave it like it is and leave your network separated from his.

---

### Post by nariub on 2011-12-29
Aside from all the design issues...

If you have router1 connected to the "big I" Internet
and router2 serving a separate private subnet.. that uses router1 to access the "big I" Internet.

fine..
from the point of view of router2.. your router1 and its local private IP space *is* the "big I" Internet.

so you will have to set up port forwards and stuff on router2 to access stuff behind router2 from the private ip space of router1..
just like you would if you were on the "big I" Internet.

imagine.. 
"big I" Internet <--> 
            Router1 <-- Private LAN #1 --> 
                 Router2  <-- Private LAN #2 --> 
                        Server B

port forwards on Router1 allow "big I" Internet to access devices  on LAN #1 behind Router1's NAT.

port forwards on Router2 would allow LAN #1 to access devices  on LAN #2 behind Router2's NAT.

carefully matching port forwards might even allow "big I" Internet access to devices on LAN #2 through two NATs.


It is easier to congeal LAN #1 and LAN #2 into a single broadcast domain but it depends on the trust and coordination between the two enitities  (you and your cousin)..  if you behave well together one router/nat/port-forward is much easier to maintain than two and the mapping between the two.

---

