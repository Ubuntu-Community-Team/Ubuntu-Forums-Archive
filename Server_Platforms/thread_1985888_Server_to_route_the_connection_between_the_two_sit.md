---
title: "Server to route the connection between the two sites"
date: 2012-05-23
forum: Server Platforms
---

### Post by DoubleJ74 on 2012-05-23
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

### Post by nothingspecial on 2012-05-25
*Thread moved to **Server Platforms**.*

Also renamed to reflect the question.

---

### Post by spynappels on 2012-05-25
I guess you could set up an OpenVPN server on the rented server and route intra-site traffic through this.
As initially the only traffic would be tunnel based traffic, you could lock it down pretty tightly using an iptables script allowing very limited access from the wider net (only OpenVPN port and possible a SSH port)

You also do not want to use Telnet as it is completely insecure. Use SSH and use key based authentication.

If you gave a little more detail on what you want to route through this intermediate, we could maybe be a little more specific.

Regards,
Stefan.

---

