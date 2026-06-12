---
title: "Cannot access outside network"
date: 2007-10-12
forum: Server Platforms
---

### Post by godsfshrmn on 2007-10-12
I am trying to access my webserver from the outside network. I can access the computer using its network IP from this PC just fine, but when I try to use the router's IP (68.209...etc) it tells me the connection was reset. I ensured that the port 8080 is open (since I changed it) in the router config.

---

### Post by k_grdn on 2007-10-12
Hi godsfshrmn,

I'm assuming your webserver is behind your router?

Does your router support NAT? IPtables?

If so you need to preroute 68.209...:8080 to webserver:8080 and forward the traffic between the interfaces.

Regards,

k_grdn

---

### Post by godsfshrmn on 2007-10-12
Is that the same as port forwarding / port triggering? If not, is that a static route? I'm not really up to par on networking. I have a netgear WGR614. I have port 8080 forwarded to the server's IP.

---

### Post by MJN on 2007-10-13
> **godsfshrmn said:**
> I am trying to access my webserver from the outside network.

Where exactly are you performing the test from?

If you are doing it from inside the LAN, attempting to use your external WAN address, then you have likely stumbled into the fact that many consumer-grade NAT routers do not support so-called 'NAT loopback'. That is, they are unable to allow internal (private addressed) clients to connect out through the router and back in to another machine. This is usually due to their architecture of running incoming and outgoing connection paths independently.

The solution to this are a) always use the internal IP of the machine you are trying to connect to (to continue to use named URLs will require either split DNS or customised hosts files), b) see if anyone has released any firmware which allows NAT loopback for your device (I wouldn't hold your breath because...), or c) buy a different router (and tell Netgear why you've switched vendors (most D-Links support NAT loopback)... you never know they might listen and start producing hardware we actually need).

The best test of external connectivity is from genuinely outside the network e.g. send one of us your address and we can try and connect.

Mathew

---

