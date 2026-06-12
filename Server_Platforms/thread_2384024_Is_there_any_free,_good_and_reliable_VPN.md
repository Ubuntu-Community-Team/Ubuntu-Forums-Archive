---
title: "Is there any free, good and reliable VPN?"
date: 2018-02-01
forum: Server Platforms
---

### Post by jl2414 on 2018-02-01
I'm looking for a free, good and reliable VPN...

I would be very grateful if links is included.

---

### Post by QIII on 2018-02-01
Hello!

Do you mean a provider, or a package to install on your machine?

---

### Post by jl2414 on 2018-02-03
Both, if possible, would be excellent.

---

### Post by jl2414 on 2018-02-03
I found a few (provider I think):
openVPN
SurfEasy
Opera 40
libreSwan
Tunnelbear
PIA

I registered in openVPN but was not able to understand how to use it.

---

### Post by wildmanne39 on 2018-02-03
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by TheFu on 2018-02-03
> **jl2414 said:**
> I found a few (provider I think):
openVPN
SurfEasy
Opera 40
libreSwan
Tunnelbear
PIA

I registered in openVPN but was not able to understand how to use it.

I use PIA (paid $35/yr) and openvpn ($0 self-hosted).  Both are openvpn-based, so the same client program is used, just different configs.

With PIA, they provide the configs to be used and the servers which the client can connect around the world with different cipher/encryption capabilities.  I tend to use PIA when at home and I want to appear like I'm in a different location.

With OpenVPN, you have to create all the certs, configs, and run the server.  There are many configuration options which can be difficult for anyone not good with networking and Unix commands.  I use this to connect to my LAN from anywhere in the world from Linux and Android clients.  VERY few people, even Linux people, would have the desire to learn to set this up.

There are many openvpn step-by-step guides, but these usually make assumptions about what the reader wants. None of them fit my needs, so I had to read, read, read and do some trial and error to get it working the way I needed.  I also had to alter some security settings on my LAN and for other self-hosted servers to make everything work.

Clear as mud?

I would be inclined to avoid free VPNs, since* if you aren't paying for a service, then YOU are the product.*  I'd rather not be the product or have my data be what these providers sell.

---

### Post by jl2414 on 2018-02-04
Thank you The Fu,

I read your explanation about "[SIZE=2]General risks of hosting a VPN[/SIZE]" and "Where to save backup?" and another post of yours about VPN.
It helped me quite a lot to understand the risks of free VPN.

Again, thaks a lot.

---

