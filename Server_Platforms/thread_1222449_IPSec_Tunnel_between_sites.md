---
title: "IPSec Tunnel between sites"
date: 2009-07-24
forum: Server Platforms
---

### Post by cbreaker on 2009-07-24
Hello,

This is very easy to do with OpenVPN, but I want to try IPSec to see if the performance is any better (been running into some performance issues on OpenVPN.)

This is the scenario:

Ubuntu 9.04 Server (192.168.5.43)
|
Verizon Router (192.168.5.1)
Dynamic Public IP (DDNS in use - sitea.company.com)
|
Internet
|
DD-WRT Router (192.168.0.1)
Dynamic Public IP (DDNS in use - siteb.company.com)
|
Ubuntu 9.04 Server (192.168.0.43)

I want to create a tunnel between site A and site B.  Trying to use OpenSWAN.  I don't even know where to start with this thing.

Here's a config I tried to use:

conn sitea-siteb
    left=192.168.5.43
    leftid=@siteavpn.company.com
    leftrsasigkey=(omitted)
    leftsubnet=192.168.5.0/24
    leftnexthop=siteb.company.com
    right=192.168.0.43
    rightid=@sitebvpn.company.com
    rightsubnet=192.168.0.0/24
    rightrsasigkey=(omitted)
    rightnexthop=sitea.company.com
    auto=add

The connection is added but never runs - it times out.  I've forwarded port 4500 UDP on both routers.   As far as I know, that's all that should be needed with NAT-T..

But I don't even know if I have the options in the right spots.  It's really frustrating - the examples on the OpenSWAN site assume both routers are on the same subnet!

I've been doing google searches for hours and hours and I just can't make any progress here.

As I understand it, OpenSWAN isn't exactly DDNS friendly, but I should be able to work around that later.   But I need to use a DNS name, not an IP address, for the other site.

Can someone please point me in the right direction?  I consider myself good at networking things but this is ridiculous.

---

