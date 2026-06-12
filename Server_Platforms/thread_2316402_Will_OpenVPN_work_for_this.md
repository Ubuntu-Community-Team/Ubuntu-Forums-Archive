---
title: "Will OpenVPN work for this?"
date: 2016-03-07
forum: Server Platforms
---

### Post by uRock on 2016-03-07
I am preparing to install and set up OpenVPN in Ubuntu 14.04 LTS. My sole purpose for this install is to allow me a secure way to enter my network via my Android phone and view my Motion server feeds, without opening my Motion server to the public.

Will OpenVPN allow me to enter my internal IP address into my phone's browser as if I were on my LAN?

Cheers & Beers,
uRock

---

### Post by papibe on 2016-03-07
Hi uRock.

Yes it will.

A few thoughts:

You would have to open ports in your router, and forward them to your server. Lately, I've been working on a configuration so that no ports are needed. I setup a VPS on the Internet. The home server calls and connects to the VPS using [tinc VPN]("http://www.tinc-vpn.org/"). In order to get access to the home server from outside, I also connect to the VPS over tinc.

You can get access to the whole LAN, but you can also _just_ give access to one port on the server.

I imagine similar setups are available for OpenVPN.

Just some thoughts. Let me know if you want to learn more about tinc.
Regards.

---

### Post by uRock on 2016-03-07
Thanks papibe! I've just started looking into tinc. I'll drop back in if I run into any questions. I probably won't set it up until I get Ubuntu 16.04 installed.

---

### Post by darkod on 2016-03-08
But wouldn't going over a VPS introduce more latency/delay? Instead of going straight to your router you are going over another machine, maybe even in another country/region...

And that doesn't improve security. For openvpn you need only one port open and forwarded on your router and you need the same on the VPS. The VPS being public needs a firewall and you still have to open the openvpn port on this firewall. I might be wrong but I see no real benefits, only downsides...

Not to mention the cost for the VPS too if you add that up.

---

