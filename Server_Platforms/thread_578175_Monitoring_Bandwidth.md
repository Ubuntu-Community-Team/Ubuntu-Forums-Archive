---
title: "Monitoring Bandwidth"
date: 2007-10-17
forum: Server Platforms
---

### Post by Bofur on 2007-10-17
Hello, I was just wondering if there were any program or some other way I could monitor who is on my router, and how much bandwidth they are using. I'm kind of a newbie when it comes to networking so I'm sorry if there is an obvious way to do it. I have a Linksys Wireless-N router. Thanks for the help in advance!

---

### Post by kidders on 2007-10-18
Hi there,

There is no obvious way to do what you described, I'm afraid. Routers manipulate network data at the packet level, so they have access to very little information about what's passing through them. Having said that, it is often possible to calculate who's exchanging information over one ... if you don't mind me taking *my* network as an example:

I have a PC acting as a router between two networks (ie what you might describe as "inside" and "outside"). Everything on the "inside" has fixed DHCP-assigned IP address, allocated by the router, so I can equate packet source & destination addresses with the computers they point to. As a result, I could use iptables to count packets to/from each DHCP-registered location, and perhaps serve that information to my network with apache, or something.

Unfortunately, the further away you get from that network layout, the more difficult the task becomes.

The other thing that can complicate matters is your definition of "who" ... ie exactly what you mean when you say "monitor *who* is on my router". In the scenario I've been describing, the idea of a "person" either has to be irrelevant, or obvious once you know what *computer* is exchanging data. To be any more sophisticated than that, you'd have to go down the authenticating proxy road ... which is not normally desirable.

A proxy is a very high-level application, so you'd essentially have access to *all* the information available about a particular network connection. The down-side is that every single network connection made by a computer you wanted to monitor would have to be "proxyable", if you wanted to take its bandwidth consumption into account. Many connections simply can't be proxied ... others only with difficulty ... some are trivial. However, at a potentially significant cost to client-side usability, you would be able to identify individual people, for the purpose of counting their bandwidth usage.

One additional concern is *why* you want to monitor network usage in the first place. If your reason for wanting to do so has any sort of security dimension, that changes things somewhat. Anyhow, if you could describe in a little more detail exactly what you'd like to achieve, and provide some topographical information about your network, I'd be happy to be a little more specific about what would be possible, and how you might go about it.

---

