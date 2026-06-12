---
title: "openVPN: routing vs. bridging"
date: 2010-04-21
forum: Server Platforms
---

### Post by tumandro on 2010-04-21
Just curious to see what everyone's opinion on using routing vs. bridging for openVPN. I'm installing openVPN on a linux box that I'm using as a router. What I was wondering was your opinions on which one of these two options to use.

---

### Post by spynappels on 2010-04-21
I use Routing on my OpenVPN servers as I want to have a large pool of IPs available on different subnets, but I want some of these clients to talk to each other, even though they may be on different subnets. 

I don't want all of my servers to be on the same subnet as my main office, and I also want to be able to route traffic from branch offices to other branch offices and main office while all having their own LANs.

Pushing routes can all be automated in the server.conf file.

Just my 2 pence worth.

---

### Post by koenn on 2010-04-21
I prefer routed vpns for the same reason as spynappels :
once the tunnels are set up, you can just route between them any way you like, just like you would with other networks or subnets, and you can treat all subnets, vpn or not, the same (in terms of routes, firewall rules, ...)

bridging somewhat messes with that model, so I'd only use it for situations where routing doesn't cut it. I haven't come across any yet.

---

