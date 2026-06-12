---
title: "Advice needed"
date: 2012-05-22
forum: Server Platforms
---

### Post by DoubleJ74 on 2012-05-22
I am in need of advice. Please maybe some of you can give me some pointers. I'm newbee in linux.
Scenario: currently i have two sites connected via ipsec connection. The latency of the default route over the internet is not satisfactory, so i want to reroute the connection via another geographic location.
I'm planning to rent a server in a particular country, which will run ubuntu server and preferably: a single nic (two is optional).
The rented server should route the connection between the two site, and also any other connections on different ports between the two sites as well. The rented server is directly connected to the internet and not behind a firewall, but should be made as secure as possible.
The routing should be done based on the source ip addresses/dns name to target ip/dns name, so the router can not be used by other source ip's (i know it is not waterproof, but this is solved at the sites).
The rented server must be remotely manageable from one of the sites(telnet?).

The rented server might in the future also be used to route from sites to other parts of the internet(non-vpn), and maybe run a small website (therefore port 80 should be excluded from the routing).

I am able to configure this scenario on a windows environment, but don't know how to do it on ubuntu.
Please practical comments only.

Thnx in advance.

---

### Post by DoubleJ74 on 2012-05-23
Posted it in the general help, because no replies here.

---

