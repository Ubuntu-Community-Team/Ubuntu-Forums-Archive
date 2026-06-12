---
title: "Selective VPN via local proxy?"
date: 2012-03-17
forum: Security
---

### Post by PsychoMike on 2012-03-17
I'll start by saying that I've used the following VPN setups successfully in the past:

- straight VPN connection, all traffic goes through VPN

- VPN with tweaked routing, only traffic for certain IP ranges goes through VPN, everything else over standard connection

The latter has served me pretty well for telecommuting. All work traffic can go through the VPN without impacting non-work traffic. The biggest problem with it is having to manually specify IP ranges.

I'm in a new situation now where I need to do something similar but with more flexibility. I have many intranet sites I need to access, scattered across many different IP ranges, with no comprehensive list of either. 

I won't get into all the ugly details, but I would very much like a setup along the lines of two separate web browser instances, one connecting through the VPN and one connecting in the clear. Then I can have a "work" window and a "personal" window - nice clean task separation.

It seems like this would be best achieved by somehow setting up a local web proxy on the machine that is tied to the VPN, while still leaving everything else on the system running against my standard connection. Then I just tell the "work" browser profile to use the proxy.

I know I could solve this by using another machine or a VM to connect to the VPN and provide a proxy (since everything in that machine/VM would run through the VPN instead of trying to segregate traffic) but I don't want to run a whole separate OS install and suck all the resources that entails. Also, my dev machine is a laptop, so I wouldn't want to depend on external machines that I might have trouble accessing from wherever I am.

So does anyone know some combination of proxy config, routing or whatever that can make this happen? Maybe instead of messing with routing, drop the VPN device from the routing table entirely but specify a specific network device (the VPN device) to use in the proxy config? Feel free to get creative - I don't mind kludging things together if it works.

---

### Post by PsychoMike on 2012-03-17
Or better yet, is it possible to just tell Firefox to bind directly to a specific network device somehow? I've spent more time Googling and it seems like at least some BitTorrent clients support that, so I guess it's not impossible for an application to pull off.

---

