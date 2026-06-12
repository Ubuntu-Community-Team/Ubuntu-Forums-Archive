---
title: "lan topology"
date: 2010-02-23
forum: Server Platforms
---

### Post by zander1013 on 2010-02-23
hi,

i am adding a new server to my lan. i have a question about the topology.

right now i have the modem connected to server1.

server1 is connected to a wireless router.

my question is where should server2 connect to the network?

both server1 and server2 will have their own ip address.

should i add a switch between the modem and then connect server1 and server2 to the switch?

both servers are linux. server1 is debian lamp, server2 is ubuntu 9.10 server. i would like to experiment with server2 as ubuntu lamp or cloud configurations.

(internet)
|
switch ---- server2 (new server or cloud)
| 
server1
|
(wireless router)

(wifi computer1), (wifi computer 2), ....



can you suggest other topologies with this hardware manifest?:confused:

please advise.

---

### Post by Jeff Anthony on 2010-02-23
Does your wireless router have ethernet ports? Usually they do. If so I'd suggest bringing internet straight to the router with your 4 computers attached to that (2 wireless and 2 ethernet).

---

### Post by zander1013 on 2010-02-24
> **Jeff Anthony said:**
> Does your wireless router have ethernet ports? Usually they do. If so I'd suggest bringing internet straight to the router with your 4 computers attached to that (2 wireless and 2 ethernet).

yes jeff. the wireless router does have 4 ethernet ports. 1 is in use as shown in the diagram Scenario 4 under "network setup options" on this link... [http://download.excito.net/web/BubbaTwo/UM-ENG/index.html#](http://download.excito.net/web/BubbaTwo/UM-ENG/index.html#)

Scenario 4 is how the wlan is configured now.

so i am guessing the topology should look like this...

(cable modem)
   |
(debian server1) <---- in firewall, dns, server mode.
   |
(wireless router)
    |
(ubuntu server2)

and i don't need a switch.

i want the new server to serve its own web site.

server1 serves [http://alonzofretwell.com](http://alonzofretwell.com) already. i want server2 to serve [http://temporalmills.com](http://temporalmills.com)

i have ordered another static ip address for server2 (server1 has its own now). is it possible for me to use the ubuntu server with its wireless adapter? the new server is run by ubuntu server 9.10 installed on an ibm t60 laptop with a wireless adapter.

it works on the network now with dhcp using its wireless adapter. i can surf the web on it and i can ping the new ubuntu server from another computer but it does not show up on the network in the place>network window.

please advise.

thank you.

---

### Post by zander1013 on 2010-02-26
the solution is to use the wireless network adapter with the wlan in its current configuration.

---

