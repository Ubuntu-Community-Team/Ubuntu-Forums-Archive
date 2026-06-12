---
title: "Sniff all traffic on home network."
date: 2006-01-13
forum: Server Platforms
---

### Post by Endwin on 2006-01-13
Greetings,

I have a home network setup with 8 computers (4 wireless 4 wired), connected to the net through a single wireless router. I would like to be able to see ALL packets that are on the network. I have installed ethereal for the packet sniffing. However as the router switches traffic (and data is not sent to everyone), and I have looked into arp poisoning with dsnif using arpspoof however this doesn't work well/long. 

Essentially I am looking for a good way to see all packets on a switched network, and is there a better/more stable/whatever solution other then trying to arp poison my router so all traffic comes to me first?

Thanks!

---

### Post by Koybe on 2006-01-13
The only possibility to get the packets : be on their way. If it's switched, it's not possible to watch all the traffic (posining puts you in a path... not all).
The only thing possible : having a switch who can transmit all the traffic trough one port. Or putting a computer between the modem and the local switching area.

---

### Post by Azion on 2006-01-13
Makes sense, although I thought there was a program you could get to capturee packets

---

### Post by Mr_Grieves on 2006-01-14
If you're connected to a regular home switch it could be difficult.
More advanced switches lets you mirror traffic on a port.

You could do diffrent exploits of the switchs mac address handling, but that will effect all network traffic going thru it, so, it's not a good idea.

You're best of using a mirror function, and if you're switch does not have one, buy a switch that does. 

You might wanna do like this.. wich is a alternetive.

Computers--Switch--Sniffer/Gateway--Internet

Configuring a box to be both gateway and sniffer.. Would probably work ok but it's not optimal for performance or security. You're best off with a switch that has mirroring capabilities, abit more expensive than just configuring some box to be gateway & sniffer.

I'd recommend using Snort. It's a NIDS, Network Intrusion Detection System.. abit more than a sniffer.

You could buy a cheap hub that you connect between you and the Internet and the switch.

Computers--Switch--Hub/Sniffer--Internet

But be aware that you with the hub solution are creating a half duplex bottle neck, wich in turn again will affect all you're network traffic. You will start to get loads of collisions and etc other problems.. not recommended.

---

### Post by djhedges on 2006-03-20
Theres also taps which they make for networks and IDS systems.  These can be kinda expensive but you could place one between your cable modem & router.

---

### Post by h3llfyr3 on 2006-03-21
Three options 
#1 span the port on the switch.
#2 Install a proxy server on the network so all traffic gos through it then sniff on the proxy server.
#3 You could ARP spoof the default gateway so all traffic goes through you but i don't recommend it as if you don't configure routing correctly you'll DOS the network.

---

