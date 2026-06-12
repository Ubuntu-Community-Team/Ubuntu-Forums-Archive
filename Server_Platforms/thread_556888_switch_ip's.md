---
title: "switch ip's"
date: 2007-09-21
forum: Server Platforms
---

### Post by Dan Mip on 2007-09-21
I've got 26 ip's on my box over a 3 subnets, how do I set it up so that I change the outgoing ip "on the fly" as it were? any pointers?

lts 6.06 | already ahve the ip's in as static's just need to switch them quickly..?

That was an incredibly short post for me :|

---

### Post by Dan Mip on 2007-09-22
think round robin dns and reverse it..? anybody?

---

### Post by HermanAB on 2007-09-22
No, I think what you need to do is set up some routes.

See the Advanced Routing Howto at tldp.org.

Cheers,

Herman

---

### Post by Dan Mip on 2007-09-22
Okay I've read that and no further forward.. here's my set up:

eth0 can be ignored, thats for internal use only..
eth1 is for incoming and outgoing inet traffic, it has 2 primary public ip's and 12 secondary public ip's.

The server is primarily a webserver dns all configured etc, what I need to do is the equivilant of

ip route add equalize default
nexthop via xx.xxx.xx.8 dev eth1
nexthop via xx.xxx.xx.12 dev eth1
nexthop via xx.xxx.xx.23 dev eth1
nexthop via xx.xxx.xx.42 dev eth1
nexthop via xx.xxx.xx.19 dev eth1

you'll note though that this is all going out of the same eth interface, id being that http request one shows ip: .8, request 2 shows .12 and so on..

can't see how to do this with  ip route, and everything I've tried results in a RTNETLINK file exists error, which is most descriptive!

more of an ip balancing issue than a load balancing issue

note: this is for OUTGOING not ingoing packets..

---

### Post by HermanAB on 2007-09-22
IPtables also has a form of load balancing built in.  I can't remember the details - you'll have to go to Rusty Russel's web site.

---

