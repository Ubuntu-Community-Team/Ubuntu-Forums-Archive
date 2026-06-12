---
title: "How to use Squid as Proxy and Cache Only"
date: 2012-01-07
forum: Server Platforms
---

### Post by mkhurram92 on 2012-01-07
hello there,

i am using Squid as a proxy and cache server installed on Ubuntu.
i want to make such an environment that all traffic passes through my Proxy Server(Squid) and then pass through our company router.
I mean just for caching and Proxy i m using Squid with one LAN Cable just.

how i can make this setup ?

Note: Squid is not a gateway server, It will be used just for cache and proxy and will pass all traffic to Cisco router 

Thanks

---

### Post by elico on 2012-01-07
there are couple of options.
or to intercept the traffic on the cisco and redirect it to the squid server.
the other option is to use wpad and other autoproxy config.

you can lookup on some options here.
[http://wiki.squid-cache.org/SquidFaq/InterceptionProxy](http://wiki.squid-cache.org/SquidFaq/InterceptionProxy)
it's really long but with index you should find yourself.

---

### Post by d3v1150m471c on 2012-01-07
easier to just use tor, no? there is a dns tutorial for using tor only to resolve domains so that you don't leak queries on my link below. if strong anonymity is not a priority you can use tor and djbdns/dnscache.

---

### Post by SeijiSensei on 2012-01-09
> **mkhurram92 said:**
> i want to make such an environment that all traffic passes through my Proxy Server(Squid) and then pass through our company router.

If you have control over the network architecture, you can run a Squid proxy server in transparent mode between the Cisco and the internal network.  Build a box with two network cards, connect one to the Cisco with a shared private address space, then connect the other one to the LAN.  Make the LAN interface the default gateway for all clients (usually through DHCP).

Now do a Google search for "squid transparent proxy".  You'll find you need to add a couple of iptables rules to the squid box and add the word "transparent" to the http_port directive in squid.conf.  Works like a charm.

I've just rebuilt a gateway for a client in the healthcare industry.  In the past we blocked dangerous objects (.exe, etc.) with regular ACLs in Squid.  This time around we've added an additional layer of protection using Squid 3 with the [squidclamav]("http://squidclamav.darold.net/") connector.  That enables Squid to scan every incoming object with ClamAV.  We also have an elaborate set of ACL rules to control access via IP address.

It's not mandatory that the squid proxy sit between the LAN and the external router.  It's possible to have the router redirect HTTP traffic to the squid box.  I just find it a lot easier to put the proxy in-line where I can manage all the traffic with iptables and squid.

---

### Post by mkhurram92 on 2012-01-12
pls guide me step by step how i can configure squid as shown in image attached. i have just one Network card.

---

