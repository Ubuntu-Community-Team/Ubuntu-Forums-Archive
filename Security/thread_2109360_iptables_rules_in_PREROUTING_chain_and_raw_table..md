---
title: "iptables: rules in PREROUTING chain and raw table."
date: 2013-01-27
forum: Security
---

### Post by kleenex on 2013-01-27
Hi, is there any reason, for creating iptables rules in [COLOR=Green]PREROUTING[/COLOR] chain and [COLOR=Green]raw[/COLOR] table? I'm asking, because: the packet entering the firewall is inspected in[COLOR=Green] PREROUTING[/COLOR] chain to see whether it requires destination  modification etc, right? So, we can block some scanning types or whatever, right before packets will arrive to the [COLOR=Green]INPUT[/COLOR] chain.  It seems to be a good idea (e.g. from security point of view) to do something like:
```
[COLOR=Navy]iptables -A PREROUTING -t raw -p tcp --tcp-flags ALL NONE -j DROP[/COLOR]
## or also
[COLOR=Navy]iptables -A INPUT -t filter -p tcp --tcp-flags ALL NONE -j DROP[/COLOR]
```What do You think? It is better to leave [COLOR=Green]PREROUTING[/COLOR] chain or to create some rules in it? What else (interesting) can be done with other iptables chains, tables? Let say, that we are speaking about typical Desktop here.

---

### Post by Doug S on 2013-01-28
> Let say, that we are speaking about typical Desktop here. Then I would assume it is not a router, and typically not used for any forwarding. In that case all packets should end up in the INPUT chain anyhow.> What do You think? It is better to leave [COLOR=green]PREROUTING[/COLOR] chain or to create some rules in it?It is an interesting question that you raised. However, myself, I don't see any good reason to do it in the raw table PREROUTING chain. The kernel would have to load another module, which I suppose is O.K.> What else (interesting) can be done with other iptables chains, tables? Oh my, but that is much to broad a question to be answered here. On my network my iptables rule set implements: The firewall; The router; Sometimes a connection rate limiter; An SSH attack bad guy detector; A bad guy IP address blacklist packet dropper; Bi-directional RFC1918 packets escaping or incoming protection...

---

### Post by kleenex on 2013-01-28
Hi **Doug**. Thank you for your answer. Some time ago, I read that the use of the [COLOR=Green]PREROUTING[/COLOR] chain is... okay, because of the reasons, which I've mentioned etc. Frankly, I never used the [COLOR=Green]PREROUTING[/COLOR] chain when it comes to typical Desktop. I would like to know if it is something good.

---

### Post by bodhi.zazen on 2013-01-29
> **kleenex said:**
> Hi **Doug**. Thank you for your answer. Some time ago, I read that the use of the [COLOR=Green]PREROUTING[/COLOR] chain is... okay, because of the reasons, which I've mentioned etc. Frankly, I never used the [COLOR=Green]PREROUTING[/COLOR] chain when it comes to typical Desktop. I would like to know if it is something good.

The simple answer to your questions have been answered. On a Desktop there is no need for PREROUTING or RAW.

The routing tables are used by routers.

The raw table is rarely used and was added to add exceptions to iptables.

I suggest :

[http://fedorasolved.org/Members/kanarip/iptables-howto](http://fedorasolved.org/Members/kanarip/iptables-howto)

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

[http://security.maruhn.com/iptables-tutorial/x4156.html](http://security.maruhn.com/iptables-tutorial/x4156.html)

From the last link > The raw table is mainly only used for one thing, and that is to set a mark on packets that they should not be handled by the connection tracking system. This is done by using the NOTRACK target on the packet. If a connection is hit with the NOTRACK target, then conntrack will simply not track the connection. This has been impossible to solve without adding a new table, since none of the other tables are called until after conntrack has actually been run on the packets, and been added to the conntrack tables, or matched against an already available connection. You can read more about this in the The state machine chapter. 

---

### Post by kleenex on 2013-01-30
Hi **bodhi.zazen**. Thank you for your answer. Your answer is simple and gets the point of this thread. Also thank you for the links. For sure, they will be useful. 

Best regards, **bodhi** and **Doug**!

---

