---
title: "Proxy server/network configuration question"
date: 2007-04-08
forum: Server Platforms
---

### Post by knorr.orange on 2007-04-08
I currently have a squid (plus squidGuard) configuration running on Ubuntu Edgy Server.  It is working perfectly, but now I want to modify it to act as a transparent proxy.  I am not sure what to do to accomplish this though.  Here is a ASCII-art diagram of how I would like to have this configured:

[FONT="Courier New"]ISP-provided router ---> ((eth0) linux server (eth1))  ---> switch  ---> several clients[/FONT]

My only goal here is to force clients through the proxy.  I don’t mind setting up each client if that makes the configuration easier.  As long as users cannot find a way around the proxy I am happy.  So it does not need to be a transparent proxy, there just needs to be no other way to the Internet.

It is also worth noting that the router our ISP provided already does NAT and DHCP so if that helps make anything easier I wouldn’t mind taking advantage of those features as long as the above requirement can still be met.

I would greatly appreciate it if someone could explain the pieces I need to implement to get this working.  Thank you!

---

### Post by kidders on 2007-04-09
Hi there,

As you rightly suggest, transparent proxying is one of two options. The second has to do with one of the fundamentals of network configuration. Consider, for example:[LIST=1]
[*]A local DHCP client wants to check his email, or visit www.google.ie.
[*]A DNS lookup is performed, to identify an IP address for pop.gmail.com or www.google.ie ... or whatever.
[*]The machine realises (a) that it's not in the same subnet as the target IP, and (b) that it has no direct route to it.
[*]Out of a lack of anything better to do with them, outgoing packets are routed toward the default gateway specified by the DHCP server that configured the machine.[/LIST]If that default gateway had no internet access (or was configured not to provide it), network clients would be forced to use proxies to get outside the LAN. Many networks (usually large ones) use this type of configuration.

On the other hand, transparent proxying has the advantage of being slightly easier to set up in domestic environments, where crappy DHCP servers (often built into DSL routers) are being used, and so on. The easiest (but not the *only*) configuration involves...[LIST]
[*]One PC with a direct route to the internet, and two network cards, acting as a firewall between the "outside" and the "inside".
[*]The second network card is plugged into a switch/router/hub on the LAN side.
[*]The firewall runs Squid (on port 3128, for example), configured to run transparently.
[*]It routes all LAN -> Internet packets on certain ports (eg 80) to itself on port 3128.
[*]As a result, network clients' internet connections are proxied, even though they are unaware of it.[/LIST]The main problem with transparent proxying follows from that last point. Most of the time, client software needs to know its connections are being proxied, so it can modify its behaviour slightly. Software that is not intelligent enough to account for transparent proxying will run into problems on occasion. Having said that, I proxy transparently with only *very* occasional problems.

I'm curious about the size of your network, mostly because creating what you might call the "perfect" setup may simply be more trouble than it's worth for you. It would go something like this:
[LIST]
[*]Configure your DSL modem to bridge mode ... essentially you would be turning it into nothing more than a modem.
[*]Set up DHCP, DNS, Proxying, PPPoE (or whatever your ISP uses), iptables, etc. on a Linux box, and have it take over complete control of your network.
[*]Sit the Linux box between your modem and your network.[/LIST]Under circumstances like those, configurations like you describe are very easy to set up (however you might choose to do it), because you have direct control over everything that's going on.

All the choices are yours to make though ... I hope there's something in here that helps.

---

### Post by knorr.orange on 2007-04-15
Thank you for your post.  I am sorry for my delayed response.

So to answer about our network size:  Currently we have a small network of 12 computers, although it may increase to around 50.  Also, about our router, I should point out that we have no control over it.  I know that is not a good answer but it is the situation we are in and we do not have much choice to change providers.  So changing settings or disabling capabilities are unfortunately out of the question for us.

I get the impression that our router restrictions will make your first suggestion no longer possible for us.  From what I understand that option only works if the device does not provide any services and the clients are stuck going to the Linux box.

If that is in fact the case I suppose it makes the decision easy:  All clients and eth0 of the Linux box are on the switch and eth1 of the Linux box has a direct connection to the router device we are stuck using.  I am still not clear on what functionality I will need to add to the Linux box though.  Also, given that we are stuck with the ISP-provided router features staying on, can I still utilize any of those features (DNS, DHCP, NAT) with this configuration?

---

### Post by kidders on 2007-04-16
Hey again,

Not being able to tweak your ISP-provided hardware has no real impact, other than making things slightly more complicated at a conceptual level ... which is not normally significant, unless you want to run servers, or set up VPN connections, etc.

Most ISP-provided DSL modems contain internal DNS & DHCP servers, handle NAT, and so on ... so all a normal "i-just-want-it-to-work" home user needs to do is plug computers straight into it, and he's done. My suggestion for you involves duplicating all these services (which is why it would be naturally desirable to turn the modem's copies of them off), but you don't *have* to. Do bear in mind that the following is what you might call a "best practice" suggestion ... if you would like to try something else, I can help you with that, too...


Consider that your modem has two NICs, one of which has (what we think of as) a direct internet connection, and another that it uses to share it with a network. Imagine your Linux box was the only client on that network. The Linux box also has two NICs ... one has (what we think of as) a direct internet connection, and the other shares it (again!) with a network. So, regardless of how much (or how *little*) control you have over your modem, you can exercise *complete* control over how your local network uses it. This configuration may seem inefficient, but it has a number of advantages. For instance, it would be completely portable (ie it would continue to work almost exactly "as is", should you change ISP at some point in the future).

Anyhow, enough theoretical explanation!

Essentially, you would now run DNS & DHCP servers, Squid, Iptables (NAT/firewall/router), and whatever other network management software you liked on your Linux box. Your network would have no choice but to go through it to gain access to the internet, and you could apply any restrictions you wanted.

---

### Post by knorr.orange on 2007-04-24
Thanks for the post kidders, I'll be working on setting up the servers.  Glad to know my configuration isn't too strange.  For anyone else following this post, once I get this all done I'll post the results and what I did on this thread.

What's funny about the whole deal is that I know our router/modem device is running Linux and everything discussed here.  So like you said, quite redundant.

A question about the IP addresses though:  The ISP-provided router uses 192.168.1.1 but I would like to also use that for my Linux server router.  My first thought is that I can't do it and should just use 192.168.0.1 instead.  However is it possible to use 192.168.1.1?  If it's only eth0 that is connected to the ISP-router then I am thinking perhaps it doesn't matter.

---

### Post by kidders on 2007-04-24
> **knorr.orange said:**
> The ISP-provided router uses 192.168.1.1 but I would like to also use that for my Linux server router.That's an odd request! People don't usually have IP addressing preferences ... you should have no reason to ever know them, once your network configuration is finished, so what they are tends not to be important.

Not only should you _not_ reuse the same IP address, but every distinct network in your final setup must have a unique subnet, so 192.168.**_0_**.1 isn't necessarily safe to use either. The only exception to either rule is where you are experienced enough to be completely sure you have imposed enough packet routing restrictions to ensure that any clashes won't matter ... but tbh, there is no reason to to try to do what you describe.

---

