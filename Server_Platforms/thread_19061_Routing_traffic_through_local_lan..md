---
title: "Routing traffic through local lan."
date: 2005-03-10
forum: Server Platforms
---

### Post by tvlad on 2005-03-10
I was asked by a friend who has an internet cafe to help him with a problem :
He has 20 computers on a local network, each computer with a routable ip, and a server running linux. How can i configure the server, so that all the traffic between those 20 computers use the local lan, instead of using the internet bandwidth ???, cause he received complaints about eating too much bandwidth because of that.

---

### Post by rmjokers on 2005-03-10
If you dont want the 20 client machines to have access to the internet, then turn off ip forwarding in the server.  However, if the clients dont have access to the internet, you wont get much business at your internet cafe...

---

### Post by tvlad on 2005-03-10
I do want them to each have internet access, i don't want to do masquerading, what i'm asking is how can i make the traffic between those 20 computers stay within the local lan, and not going through the internet.

---

### Post by alastair on 2005-03-10
Not sure on what you really mean - but it might be as simple as making sure the 20 machines have their "default route" (i.e. gateway) set to the server.

But ... not sure what you mean. What is a "routable ip" mean? Publically routable? What is the network config? Is it just like an office LAN with a gateway/firewall connected to the internet - all others connect through the gateway?

---

### Post by tvlad on 2005-03-13
Ok, let me try to be clearer, each of those 20 pcs has a public ip, i don't have to do masquerading on the server for them to all get on the net behind ONE ip, no, each pc has it's own public ip, i don't have to do masquerading.

A local ip would be 192.168. or 172.16........

---

### Post by az on 2005-03-13
Do they each have two network cards?


Is that a stupid question?  Someone smarter than me should be answering this.

---

### Post by ubuntu-geek on 2005-03-13
You have a few options here.

1. Setup each pc to get an INTERNAL 192.168.0.x IP via dhcp from a router/gateway that is connected to the public internet. This way local lan traffic stays local.

2. Put in a second nic card to each pc and configure it for a local internal network.

Hope that helps.

---

### Post by spoetnik on 2005-03-14
I think you hve to alter the route table to prevent the machines from accessing the internet.
I don't know the syntax but route --help will probably do the trick

---

### Post by BoBoB on 2005-03-14
If each PC has a specific route to it's local network this will never happen unless the traffic is directed to an IP address outside the LAN.

You can check the default routing by issuing a "ROUTE" (or "ROUTE PRINT" in Windows)  command on each PC.
If this shows a route to the network address, ex. 192.168.1.0 with mask 255.255.255.0 and the gateway address is the local IP, and all PC's are on the 192.168.1.x network then all local traffic will be routed directly to the target PC on the same subnet.
If there is a problem with local subnet traffic being routed via internet, please post the output of the ROUTE command on one or more of the PC's in question.

---

### Post by cpinto on 2005-03-14
I don't think that ip aliases will do you any good so the best thing is to get a second nic for each machine and give that nic a static ip address... since you're only using 20 machines, a class-C IP range (192.168.x.x) will be more than enough for the following demonstration purposes:
Machine A has ip address 192.168.0.10 on eth1. To keep everything tidy inside the LAN, you must route all traffic from/to the LAN addresses with:
% route add -net 192.168.0.0 netmask 255.255.255.0 dev eth1 

Since every machine is connected to the internet by itself and you'll probably want to deploy LAN services sooner or latter, remember to turn ip spoofing rules on while setting up your iptables firewalls (one for each machine).

GL,
Celso

---

### Post by az on 2005-03-14
Why do they all have public addresses?  Maybe that is the problem.

---

### Post by sime on 2005-03-15
[QUOTE=azz]Why do they all have public addresses?  Maybe that is the problem.[/QUOTE]

Same question that came into my mind. Basically you want to get a understanding of the route(8) command, which can tell each host that all traffic must go via the server.

---

### Post by BoBoB on 2005-03-15
With a single network interface on each PC:

1. Check that the PC's are on the same subnet. (Same network id/subnet mask)
2. They all have a route to their own subnet.

Lets say the network id is 111.222.0.0 (b class network), and the network mask is 255.255.0.0.
Each PC has an IP address in the range with 111.222.0.1 - 111.222.255.254
They also should have a route to 111.222.0.0/mask 255.255.0.0 with their own IP as the gateway address (or * on Linux).

In addition they would have a default gateway to a router on the internet or a firewall or something.

With multiple network interfaces the solution may be a little different.

If the local traffic is still being routed via the internet then there is a protocol issue, maybe a proxy configuration or something like that..

---

### Post by mips on 2005-03-16
tvlad,

To provide you with a proper solution to your problem you are going to have to give us a bit more info.

Are all the public IP addresses within the same subnet range ?
What is the the subnet mask fo the adresses ?
What is the Default Gateway address on the ISP side ?
What is the IP address of the Linux server ?
Why do the PC's have public addresses ? Whats worng with Private addresses & NAT ?
Do you have a Router onsite ?

If you do not feel comfortable posting the public IP's here yuo can always PM me.

A network diagram would be nice for the section from the ISP to just before the PC's.

Cheers
mips

---

### Post by tvlad on 2005-03-16
All the addresses are under the same subnet range, let's assume they all have a subnet of 255.255.255.0

The server has two nics . One connects to the cable modem and the second to the switch . All the pcs are connected through a switch. Every pc has it's own address because people play mmorpgs on them, cs on the net, irc and so on. And no, no router if by one you're reffering to cisco or the like routers.

PS: the address isn't the one, i don't even remember it, and to tell the truth, what i'm asking now, a friend asked me to help some time ago, i didn't know how and then i got busy with school, and i thought i'd ask now, since the need may arise in my network.

I don't have a diagram, though it's pretty straightforward, all the pcs connected to one switch.

---

### Post by BoBoB on 2005-03-16
I'm suffering by missing info here, but if you run a traceroute on one client PC to another, is the traffic routed through more than one host, or does the host answer directly?

Windows: tracert [ip-of-neighbour-PC]
..should make just one hop.

Linux: traceroute [ip-of-neighbour-PC]
..should make just one hop.

If the result is more than one hop, then there is a routing problem.

If the result is one hop and traffic on other ports (like http/irc/smtp etc.) is still routed through internet then there must be a proxy setup involved.

If the result of the traceroute is several hops, then there is a routing problem, and you need to add a route to the "local" subnet on each client PC.

---

### Post by mips on 2005-03-18
tvla,

BoBoB has a good point.

I assume that you mean the cable modem address also falls within the same range as the rest of the addresses?

Where does the gateway reside, on the LAN side or on the ISP side? I'm assuming it is on the ISP side which means all the traffic will traverse the WAN(cable network) which is shared media and this is what is upsetting the ISP or service provider.

You do not supply enough info to form a solution. With the correct info this would be really easy to solve, right now i'm just poking in the dark hoping to find the cat :)

The fact that you say all the addresses(cable modem as well) are in the same range/subnet leads me to believe you are pointing your pc's towards a gateway which is not on a local LAN.

cheers
mips

---

### Post by garyng on 2005-03-18
what is the ip range of these "internal" machine ? If they are already internal(192.168.x.x for example), there is no way they can go outside unless NAT is enabled. In that case, nothing can be done because the outside traffic is what is needed(icq etc.)

I don't think local traffic will go outside if all of them are on the same subnet(regardless if they are using public or private subnet range) as that is resolved by ARP, no routing involved.

---

### Post by Abhi Kalyan on 2006-11-13
> **tvlad said:**
> I was asked by a friend who has an internet cafe to help him with a problem :
He has 20 computers on a local network, each computer with a routable ip, and a server running linux. How can i configure the server, so that all the traffic between those 20 computers use the local lan, instead of using the internet bandwidth ???, cause he received complaints about eating too much bandwidth because of that.
Hi tvlad,
Wanted to know if the following is what you are talking about.( am also in the search for a similar solution )

1. There is one server connected to the internet.
2. the server has two NIC's NIC-A, NIC-B
3. NIC-A is connected to the DSL router for internet
4. NIC-B is connected to the switch
5. NIC-A has a IP 192.168.1.2 and the DSL router has an ip of 192.168.1.1
(both having the same netmask lets assume 255.255.255.0)
6. NIC-B has an IP 10.0.0.1 and netmask of 255.255.255.0
7. All other systems on the LAN connected to the switch have IP's ranging from 10.0.0.2 - to - 10.0.0.22.
8. How to make NIC-A and NIC-B communicate with each other?
my thought is if they do cummunicate with each other, this allows intenet access for all other systems. At the same time isolating the LAN from the internet.
Please post if this is so.

Note: Im trying to see if the above can be done, and have zilch knowledge of routing other than concepts. If some one could help it would be great.

Thank you
Sincerely
Abhi Kalyan

---

### Post by mips on 2006-11-13
> **Abhi Kalyan said:**
> 
8. How to make NIC-A and NIC-B communicate with each other?
my thought is if they do cummunicate with each other, this allows intenet access for all other systems. At the same time isolating the LAN from the internet.


Well the easiest way is to Install Firestarter & enable ICS.
If you want a more technical & detailed approach look at [http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

---

### Post by Chayak on 2006-11-13
I don't think I'm the only one confused by the question initially but as I understand it you have an entire network with internet accessable IPs (ie you can directly connect to the internet with them)  If all of them go into the server then create a private network and use the server as a Squid proxy with cache.  All the local traffic will stay internal and you'll save internet bandwith by allowing the cafe computers to pull from the cache rather than going out on the internet every time.  I wish I could be more help but I don't have a clear picture of your network topology including routers etc.

---

### Post by Abhi Kalyan on 2006-11-13
thank you mips getting to the link ASAP.

---

