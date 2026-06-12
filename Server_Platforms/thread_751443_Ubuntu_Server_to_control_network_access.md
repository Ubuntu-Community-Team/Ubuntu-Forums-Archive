---
title: "Ubuntu Server to control network access"
date: 2008-04-10
forum: Server Platforms
---

### Post by agql on 2008-04-10
Hi everyone,

I work for an education center with about 120 Windows based PCs. I want to set up a "center server" with a variety of services, among other control/cache the Internet access. I have installed Ubuntu Server v7 in a computer with two network card (ethernet). I have installed also WebAdmin. The arquitecture I want is:

Inet <-> card1 - Ubuntu - card2 <-> Internal network

Questions are:

- To implement routing, do I need to create a "NetworkConnectionBridge" or simply with setting up (firewall/NAT/routing) is enough.
- Even more, if I create the networkConnectionBrigde, will Firewall rules work? or will the bridge leave all traffic (as it is a lower protocol)?
- I also want to use Squid, shall I configure it after routing is working or it is independent.

Finally,

- Does anyone know where I could find documentation that could be called as "RoutingUsingUbuntuForDummies"

Thanks indeed

Agustin González-Quel - Spain
[email]agustin.gonzalezquel@gmail.com[/email]

---

### Post by cdenley on 2008-04-10
You can set this up using nat or a bridge. I'm using a bridge for this kind of setup. Traffic can be filtered using the FORWARD chain in iptables. If you already have a router, I would set it up as a bridge.

Squid proxy is usually used for filtering and caching, but it only filters http traffic, which is why I use iptables for filtering.

---

### Post by foolano on 2008-04-13
You could try use [ebox]("http://www.ebox-platform.com") to do what you are planning. Your scenario fits perfectly with its  [design]("http://trac.ebox-platform.com/wiki/Document/HowTo/SetUpNetworkScenario").

It's pretty easy to install: Ubuntu Hardy plus* apt-get install ebox-squid * will give you what you need.

---

