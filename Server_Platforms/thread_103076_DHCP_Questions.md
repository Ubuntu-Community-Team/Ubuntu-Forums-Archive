---
title: "DHCP Questions"
date: 2005-12-13
forum: Server Platforms
---

### Post by kitchens on 2005-12-13
Let me preface by saying I'm a noob. I've run into what seems to be a unique problem. I can't google up any solutions. I work for a company that would be interested in replacing their windows based dhcp server w/ ubuntu. We are a small dialup isp but we also provide wireless internet to a gated community of retirees. Our wireless system is really pretty embarrassing. Its an 802.11b network. We have several towers beaming our 11b throughout the community. The end users have modified antennas which we mount on their homes. We regulate who can connect to the network through mac filtering. Users are assigned an address out of a block of class C ip's through our dhcp server.
The problem we have been running into happens when someone purchases a router and plugs their internet connection into the LAN side of their dhcp enabled router on accident. Then their router is spitting out 192.168 addresses to everyone on our wireless network. I'm sure our ignorance is the biggest piece of the problem but personally I'd like to move over to ubuntu as we educate ourselves.

---

### Post by cactus on 2005-12-13
I see a couple of options for your problem..but they generally all depend highly on your setup..

1) You need to filter the dhcp 'offers' coming 'from' your wireless nodes, before they reach the rest of your network. A likely solution is to put a router/packet filter upstream from your users. This would require AP node isolation, so each of your wireless clients cannot speak directly to each other via the wireless AP, but must route through the router first (the router can send traffic back down through the AP if the nodes need to talk, like for p2p traffic or something).

2) Configure the client router devices to not pass dchp offer packets upstream. An option, if you completely control those devices, and if they have that feature.

Know that this is not a unique problem you have. I know several college campuses that have this same problem in the dorms. Some student hooks up their ap the wrong direction, and brings down the connection of half the students in the building. 
Generally the problem is quickly discovered, and the port is turned off remotely (remotely managed switches). Not the most elegant solution, but when you don't control much of the endpoint (wall jack)..and are on a limited budget (no packet filters/routers for every network segment) there is only so much you can do..

Well...some ideas. hopefully others will have more.

PS. I am not liable for blah blah blah... *insert standard disclaimer*

---

