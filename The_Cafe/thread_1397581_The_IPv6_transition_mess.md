---
title: "The IPv6 transition mess"
date: 2010-02-03
forum: The Cafe
---

### Post by Skaperen on 2010-02-03
With IPv6 on my mind the past few days (see the Networking and Wireless forum here), I've also been looking at some of the problems other people have had, and recalled some past problems I have had. I've concluded that there is more than one thing broken with respect to gracefully handling the v4 to v6 transition. One is DNS servers and the other is the resolver library. The fact that interfaces are being configured with a link-local IPv6 address just muddies the water.

Ubuntu should, for now, and maybe for a while, ask (during installation's network configuration) if IPv6 is available. If not, it should leave out the IPv6 kernel modules and be sure the IPv6 link-local address is not configured. It should remain the default to have IPv6 enabled (e.g. press enter, you get that default). It should have the option to disable IPv6. An even better option is to ask the installer if she wants to perform a network test to determine if IPv4 and IPv6 are available. If the installation is on a network connected machine, do this now. It should also be an option in the network manager (whose code is this? Debian? Gnome?).

The DNS servers should get smarter. Right now they can get hung up in recursive queries when NS records have hostnames with AAAA records. If there is a live IPv6 interface, they will usually try to get the AAAA records first. This is one of the culprits in lookup delay. What they should do is try to get both AAAA records and A records nearly at the same time (add a fraction of a second delay to sending the query for the A records). When the AAAA record arrives, ask that name server the next query. If the answer to the query sent by AAAA has not yet arrived when the A record comes in, parallel ask the same query to the A record address. The timeouts run parallel, not in sequence. Whichever next answer arrives first, use it.

The DNS servers could get even smarter and discover if IPv6 even works by doing a query for some data via known IPv6 addresses, if that data is not present in cache. That data might simply be the AAAA record of a hostname known to be in a GTLD server. Cache it as usual if it arrives.

The resolver library should get smarter. It has an option to enable or disable IPv6 lookups. But this is not enough. One might want to have IPv6 addresses looked up in /etc/hosts (files in nsswitch.conf) yet NOT have AAAA records queried via DNS.

I'm currently going to work around this mess by putting a root level wildcard AAAA record in my DNS caching servers. Maybe I'll point it at my internal web server (it now has a private "unique local" address in [fc::/7]). I don't have public IPv6 access right now (my ISP charges a lot extra for it). I'll have to remember to remove that when I do get that public IPv6 access (even if via a tunnel, which most likely I will not do).

It's already going to be hard enough to get IPv6 going. Most people won't make the effort until a bunch of internet is available only via IPv6 (besides some porn, warez and craqz sites that are hiding in IPv6 space). No one is going to drop off of IPv4 as long as most of the net can't be reached via IPv6. Chicken. Egg. So we need to do whatever we can, all that we can, to get IPv6 going in a graceful and user friendly way. We need to make people want to at least turn IPv6 on, or leave it on. We definitely do not want to have to turn IPv6 off to solve problems.

---

### Post by LowSky on 2010-02-03
How is a normal user to know what IPv6 even is? So why ask them a question they can't answer?

Things are supposed to get easier. Also how many peopoe are really having an issue, I know my internet connection is fine.

---

### Post by Skaperen on 2010-02-03
> **LowSky said:**
> How is a normal user to know what IPv6 even is? So why ask them a question they can't answer?

Things are supposed to get easier. Also how many peopoe are really having an issue, I know my internet connection is fine.It would be great if it was not necessary to ask them at all. Smart enough software could accomplish that. Until then, asking is better than leaving them with problems. The question should also be explained. It should also say "If you don't know what IPv6 is, just use the default by pressing return". That default will be 'no' until either the software is smarter, or IPv6 has reached prime time (sufficiently deployed that anyone without it is in the dark ages).

---

### Post by Skaperen on 2010-02-03
It seems the biggest problem most people are having is slowdowns of their IPv4 network due to various components trying to use IPv6 when it isn't completely there. I've run into it in various cases, as have many others as reported in the Networking and Wireless forum here, and other forums elsewhere.

---

### Post by juancarlospaco on 2010-02-03
You can use IPv6 with your current IPv4:

**sudo apt-get install miredo ; ping6 -c 4 ipv6forum.com**

:)

---

### Post by jrusso2 on 2010-02-03
Currently the IPV 6 is encapsulated in IPV 4 for these compatibility reasons.

---

