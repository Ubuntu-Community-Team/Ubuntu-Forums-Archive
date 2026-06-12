---
title: "Multiple active PPOE + DHCP + web-server"
date: 2018-04-06
forum: Server Platforms
---

### Post by biosnod on 2018-04-06
Hi, I apologize for errors if they are, English is not my native language, I have a small server at home, previously it had one Internet channel, but now it wasn't enough for its speed, so 2 more Internet channels were put into the apartment, but there was a connection issue. Now I have one router (TP-LINK Archer C2), one switch (unmanaged, TP-LINK TL-SG1008D) and three Internet PPPOE channels with white external static ip-addresses (198.50.154.197, 195.10.120.121, 198.50.154.158), the first channel (198.50.154.197) is connected to the router, then the switch is connected to the router and finally the server is connected to the switch (the server only has one network card with one port). The router sends the server through the switch via DHCP ip 192.168.0.112 and forward the port to it (198.50.154.197:80 => 192.168.0.112:80). The other two Internet channels are connected to the switch, but don't work yet. If I enable one PPPOE connection from the channel in the switch, the DHCP connection from the router is turned off. How do I configure the server so that all three connections are active? - 192.168.0.112 (DHCP, external 198.50.154.197), 195.10.120.121 (PPPOE local = external), 198.50.154.158 (PPPOE local = external).


Ubuntu 16.04.5 LTS, the server is apache2 listening 0.0.0.0:80, need to work on requests for the 80th port from all three external ip-addresses:
HTTP-Request => Router 198.50.154.197:80 (PPPOE) => Switch => Server 192.168.0.112:80 (DHCP, reroute from router)
HTTP-Request  => Switch => Server 195.10.120.121:80 (PPPOE)
HTTP-Request  => Switch => Server 198.50.154.158:80 (PPPOE)

---

### Post by wildmanne39 on 2018-04-06
Hello and welcome to then forum!

*Thread moved to **Server Platforms, a more appropriate forum**.*

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Thanks

---

### Post by TheFu on 2018-04-07
Can't you just setup port forwarding on each of the external IPs through the router to a single static IP on the server?
You'll want to setup external DNS so that all three public IPs are tied to the same FQDN and in apache, you'll want to make all connections "sticky" so clients return to the IP they had last request.  For any webapp, using a sessionid would be necessary.

Almost none of this is apache configured.  It is handled by the network setup.

---

### Post by darkod on 2018-04-08
You should avoid using multiple WAN connection if possible.

If that is not possible, you should use a router that has multiple WAN ports and that way the WAN/PPOE side is not conflicting at all with the LAN side and DHCP. And the router will take care of routing correctly all incoming/outgoing traffic for you, like TheFu says...

---

### Post by biosnod on 2018-04-09
1) I realized that it was a mistake to drop my DHCP router through the switch to the provider's network
2) The site doesn't use sessionId, only cookies
3) I want to register these 3 ip addresses in DNS, the alternation will be based on the algorithm of Round Robin DNS
4) The router doesn't have the ability to change the mode for an individual port from the LAN to the WAN, so I exclude the router
5) Switch unmanaged, which means that the network of providers will be combined through a switch, which can't be done, so I exclude the switch
6) Let's say that I buy a **managed **switch, I plug these 3 channels into the first 3 ports, configure the switch so that packets are not sent between these ports (is it possible and whether this solves the problem of interconnection of ISP networks or there are still underwater gems?), I plug into the 4th port server itself (with one network card with one port) and configure so that the switch from each of the first three ports sends requests to the 4th port (the same is possible?), the server is processing requests on the 80th port and issues a response that goes back to the 4th port of the switch (through one network port with one port), and now the switch in some magical way correctly selects the port to forward the response, but it's the one from where the request came from and sends it via it (is it possible at all)?

---

### Post by darkod on 2018-04-09
A switch can't route traffic, even a managed one. If you are willing to buy hardware, consider buying router with minimum 3x WAN ports and that will solve all your problems if I understand you correctly. For example TP-Link (as a budget option), has a router model that has 1x WAN, 1x LAN and 3x interchangable ports... Which means you can have 4x WAN (up to 4 different ISP connections) and 1x LAN setup on your router. After that for your LAN you will use standard switch to allow enough ports to plug in all equipment that you need...

---

### Post by juanherrera on 2018-04-21
I think the cheapest and easy way to manage your three WAN links is to add 3 cards to your server and configure your router/s as bridge.

Some time ago i did same connections and I created this:

HOME Server with 3 NICs and ESXI installed.

ROUTER ISP > NIC 1
PPOE > NIC 2
PPOE2 > NIC 3
NIC Onboard > Switch

Create one virtual machine with pfsense to manage isp links and local network. Just with one core and 256gb ram is enough. Also Pfsense will manage load balance between isp links and you'll have firewall features to send traffic to webservers.

Then you have to create virtual machine for your servers and it's done!

Regards.

---

### Post by TheFu on 2018-04-21
At least for a router that faces the internet... 

There are important security considerations when using VMs as routers.  Bridge connections should be avoided.  Really need to passthru the entire PCI card to the router OS, so it has exclusive control.  The hostOS should have ZERO access to NICs provided to a router.

For a router on an internal LAN running inside a VM, I'd still want passthru, but wouldn't be nearly as concerned over using a bridge connection. Because of the way that bridges work, any machine on the same bridge can get access to all the traffic. That's a terrible thing if you want a secure router. Terrible.

Adding a 2-4 port Intel NIC would be my preference just to save slots, but all of them would be passed thru to the guest.  It isn't a   pick-a-port-for-passthru thing.  Whole card or nothing.  Obviously, vt-d is required in the hardware to support this. Last time I looked, most of my systems didn't support that.

I know lots of people choose to run a router on a VM, but there are things that just don't smell right.  This fails my "smell test" for being secure.  1 tiny bug is all that is needed for a VM security issue to make your entire network open. It has happened before and I expect similar methods will be uncovered a few more times.  Security plans shouldn't trust 1 single technology. Think layers.

Just sayin'.

---

### Post by LHammonds on 2018-04-22
I'm with darkod on this one.  Drop the $100 for a multi-port WAN Router.

A server-based router can work like juanherrera mentions but how he configured it makes me a TheFu agree that it was not a very secure method for doing so.  The routing "machine" needs to be separate from your "server" hardware.  Sure, you put together a routing machine and buy additional hardware for it and become an networking expert to manage it...or drop $100 on a router that was designed to do that for you.

LHammonds

---

