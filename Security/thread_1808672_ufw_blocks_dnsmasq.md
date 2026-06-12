---
title: "ufw blocks dnsmasq"
date: 2011-07-20
forum: Security
---

### Post by thk on 2011-07-20
I am using dnsmasq to proxy dns requests (NOT as a dhcp server). What that means is my firewall machine is setup to accept request from the internal network on port 53 and forward those to an external name server.

```
host <something>
```

works fine when ufw is disabled, but fails when it is enabled. I have ufw setup to only allow incoming ssh connections at the moment and it is configured to do ip masquerading.

I do not need to enable incoming packets on the domain service specifically because I am only serving a private network and those packets are all allowed already. (And opening port 53 makes no difference anyway.)

What I see in my logs is that the external name server is trying to connect to my server via UDP, source port 53, destination port <very large number>, but these are blocked by ufw.

I am wondering if anyone else has been through this and can give a quick fix.

Do I allow all incoming UDP connection with source port 53? (Makes not much sense to me.) I can certainly just allow all connections from the external name server, but that seem artificial. What's the right way to do this?

---

### Post by bodhi.zazen on 2011-07-20
> **thk said:**
> Do I allow all incoming UDP connection with source port 53?

yes

> (Makes not much sense to me.)

From your question you have a bit of reading to do on iptables, but once it sinks in iptables is very straight forward.

See:

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

You will have to allow incoming an outgoing UDP connections to your lan and from your dnsmask host to and from the internet, or you will break DNS.

[http://systembash.com/content/dns-server-firewall-open-ports/](http://systembash.com/content/dns-server-firewall-open-ports/)

Answer me this, why all those ports ?

---

### Post by thk on 2011-07-20
> **bodhi.zazen said:**
> yes

So I should let anyone sending UDP packets out on port 53 access any of my ports? That seems to defeat the purpose of a firewall.


> **bodhi.zazen said:**
> 
From your question you have a bit of reading to do on iptables, but once it sinks in iptables is very straight forward.

See:

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)


There is always more to learn. Thanks for the resource. I have relied directly on iptables for the past 10 years or so, but wanted to try ufw. (It puts the "complicated" in "uncomplicated" ;)

> **bodhi.zazen said:**
> 
You will have to allow incoming an outgoing UDP connections to your lan and from your dnsmask host to and from the internet, or you will break DNS.

[http://systembash.com/content/dns-server-firewall-open-ports/](http://systembash.com/content/dns-server-firewall-open-ports/)

Answer me this, why all those ports ?

As I said, I don't need to open 53 to everyone because I am not planning to serve the internet, only my internal network and those packets should be accepted by default. (Of course ufw inserts a ton of rules, so its a bit hard to know exactly what is going on.)

I'm not filtering outgoing packets, so no need to open those either.

What I think is happening is that dnsmasq is contacting the name server and the returning packets are landing on some high number UDP port. Should those not be state RELATED,ESTABLISHED? I though I was allowing those. Or is the name server making a new connection back to my server?

---

### Post by bodhi.zazen on 2011-07-20
The most difficult thing about iptables is the requisite background knowledge to understand what exactly is going on.

As I already gave you the information in the form of links, and as I am not going to re-type the information in those links here, and as reading the links did not help, I am not going to repeat the information.

First I suggest you start by reviewing UDP (vs TCP) and DNS.

Next figure out what the high ports mean ;)

If you simply want to block all network traffic, unplug your network card.

A firewall is not for blocking all traffic, you need to figure out what traffic to allow and what traffic to block.

Since you are blocking traffic without understanding what and why, you broke your internet functionality, in this case DNS.

---

### Post by thk on 2011-07-20
The solution was to purge ufw and reinstall. The defaults work fine with dnsmasq so it must have been one of my changes. I was able to setup forwarding and SNAT without blocking dnsmasq. I actually wonder if the problem was not caused by the limit rules in ufw. Perhaps it was blocking the external dns server because it had made too many connection attempts.

---

### Post by thk on 2011-07-20
> **bodhi.zazen said:**
> The most difficult thing about iptables is the requisite background knowledge to understand what exactly is going on.

As I already gave you the information in the form of links, and as I am not going to re-type the information in those links here, and as reading the links did not help, I am not going to repeat the information.

First I suggest you start by reviewing UDP (vs TCP) and DNS.

Next figure out what the high ports mean ;)

If you simply want to block all network traffic, unplug your network card.

A firewall is not for blocking all traffic, you need to figure out what traffic to allow and what traffic to block.

Since you are blocking traffic without understanding what and why, you broke your internet functionality, in this case DNS.

You seem rather desperate to demonstrate your expertise. Here's a hint: it only makes you look like you are compensating.

---

### Post by bodhi.zazen on 2011-07-20
> **thk said:**
> You seem rather desperate to demonstrate your expertise. Here's a hint: it only makes you look like you are compensating.

Glad you got it solved, hope you learned something of value from your experience.

In my experience, once someone understands the underlying networking principles, iptables is an efficient tool.

---

### Post by stolsvik on 2011-08-17
> **bodhi.zazen said:**
> The most difficult thing about iptables is the requisite background knowledge to understand what exactly is going on.

As I already gave you the information in the form of links, and as I am not going to re-type the information in those links here, and as reading the links did not help, I am not going to repeat the information.

First I suggest you start by reviewing UDP (vs TCP) and DNS.

Next figure out what the high ports mean ;)

If you simply want to block all network traffic, unplug your network card.

A firewall is not for blocking all traffic, you need to figure out what traffic to allow and what traffic to block.

Since you are blocking traffic without understanding what and why, you broke your internet functionality, in this case DNS.

It is simply embarrassing reading your completely ignorant reply to a person which obviously knows what he is doing. Shame on you.

---

### Post by thk on 2011-08-17
> **stolsvik said:**
> It is simply embarrassing reading your completely ignorant reply to a person which obviously knows what he is doing. Shame on you.

In my experience, people unable to suggest specifics are posing. (I think ignorant is the wrong word choice. Cheeky, unappreciative and obnoxious perhaps, but not ignorant.)

---

### Post by Iowan on 2011-08-17
Solved, done, closed...
Current discussion is unproductive, at best.

---

