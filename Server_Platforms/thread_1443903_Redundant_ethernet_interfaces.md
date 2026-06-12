---
title: "Redundant ethernet interfaces"
date: 2010-03-31
forum: Server Platforms
---

### Post by Hypnoz on 2010-03-31
In order to have server availability be redundant, I have set up two switches in each cabinet, and run an ethernet cable from both switches to each server. Both interfaces are in the same subnet, so even if one goes down the other should be able to continue the server function. Obviously only one interface can have a default gateway, but that isn't important cause pings are coming from within the subnet.

However, I am seeing some unexpected behavior with this. When I bring down a switch, availability to the server depends on whether or not the interface switch brought down was above or below the other one on the "route -n" list. Bringing down the interface switch listed 2nd in "route -n", the first interface stays up and alive. Bringing down the top interface switch in the "route -n" list doesn't allow the 2nd interface to be pingable anymore. If I switch their order (ifdown && if up the top interface, making it the bottom now), then pinging resumes.

I feel this may be a linux kernel issue not realizing the switch is gone, and failing over to sending traffic over the 2nd interface.

---

### Post by koenn on 2010-03-31
It may be a flaw, and it may be unexpected, but I don't think it really matters.

If a client connect to your server via (the ip address of) eth0, and the switch this interface is connected to goes down, the client isn't magically going to reastablish that connection via (the ip addresss of) eth1. Your switches aren't magically going to redirect traffic to a different switch port / MAC address either. 
So your redundancy won't work because you're still dealing with 2 IP adresses. 

I think the trick here is to bind the 2 interfaces so they share 1 IP address. 
Your switches would need to do "spanning tree" because multiple paths to the same destination could create loops and broadcast storms, iirc.

---

### Post by Hypnoz on 2010-03-31
I have both interfaces of a server in the load balancer, so if one interface goes down, the load balancer will detect that, but traffic will still be able to connect to the other interface.

---

### Post by fang0654 on 2010-03-31
What you want to do is set up bonding:

[https://help.ubuntu.com/community/UbuntuBonding]("https://help.ubuntu.com/community/UbuntuBonding")

It will allow you to either load balance your interfaces, or set them up for fault tolerance.  All of my servers are set up for failover, so if one stops working, the other NIC takes over automatically, same MAC address, same IP, etc.

---

### Post by Hypnoz on 2010-03-31
> **fang0654 said:**
> What you want to do is set up bonding:

[https://help.ubuntu.com/community/UbuntuBonding]("https://help.ubuntu.com/community/UbuntuBonding")

It will allow you to either load balance your interfaces, or set them up for fault tolerance.  All of my servers are set up for failover, so if one stops working, the other NIC takes over automatically, same MAC address, same IP, etc.

TY for the link, I will do some testing with this.

Do you have a virtual switch, or stacking, set up on your switches. What work did you do on your switches to get bonding to run properly?

---

### Post by fang0654 on 2010-03-31
The nice part about using the failover mode setting is that you don't need to do anything special with the switches.  I have either Cisco, Netgear, or combinations of the two in various locations, with nothing special set up.  Most of the servers I have plugged into separate switches. 

When you are set up for failover, when a NIC goes down, the server does the equivalent of unplugging the network cable from the failed card and plugging it into the backup card.

---

### Post by koenn on 2010-04-01
> **fang0654 said:**
> 
When you are set up for failover, when a NIC goes down, the server does the equivalent of unplugging the network cable from the failed card and plugging it into the backup card.

not exactly.
what you do is create a 'virtual' interface (bond0)  that refers to 2 physical network adapters. This is actually what I had in mind when i first posted.

Even though the bond itself has only 1 IP and 1 MAC, it will still be visible on 2 switch ports, which can cause trouble at layer 2.

That's why the modes where this is relevant, take precautions, eg
- mode 1: "The bond's MAC address is externally visible on only one port (network adapter) to avoid confusing the switch"
-mode 4: "Dynamic link aggregation. Pre-requisites: A switch that supports IEEE 802.3ad Dynamic link aggregation."

Spanning Tree Protocol fixes the same type of problem, but is apparently not necessary because the bonding software takes care of the issue itself.

---

### Post by fang0654 on 2010-04-01
> **koenn said:**
> not exactly.
what you do is create a 'virtual' interface (bond0)  that refers to 2 physical network adapters. This is actually what I had in mind when i first posted.

Even though the bond itself has only 1 IP and 1 MAC, it will still be visible on 2 switch ports, which can cause trouble at layer 2.

That's why the modes where this is relevant, take precautions, eg
- mode 1: "The bond's MAC address is externally visible on only one port (network adapter) to avoid confusing the switch"
-mode 4: "Dynamic link aggregation. Pre-requisites: A switch that supports IEEE 802.3ad Dynamic link aggregation."

Spanning Tree Protocol fixes the same type of problem, but is apparently not necessary because the bonding software takes care of the issue itself.

That's what I meant for mode 1 - thanks for saying it with much more clarity.

---

### Post by KiLaHuRtZ on 2010-04-01
Read my posts in this thread...:p

[http://ubuntuforums.org/showthread.php?t=1423602](http://ubuntuforums.org/showthread.php?t=1423602)

---

### Post by Hypnoz on 2010-04-05
Thanks for the ideas so far this is great info.

What I have run into is that my Cisco 2960G's can't be stacked, so I can't bond the NIC's in a link aggregate mode, but if I can get the mode 1 (failover) working, that would take care of my redundancy needs. 

Another benefit would be that the server would only have 1 IP, simplifying other parts of my design including the two ip's I have in the load balancer for each server currently.

I'll test this out as a switch failover solution and report back results when I get a chance.

---

### Post by Xipher on 2010-04-05
We utilize the failover mode for a large customer at work with unstacked 2960G switches and it works fine.

---

