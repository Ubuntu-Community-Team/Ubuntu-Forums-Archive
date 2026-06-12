---
title: "Setting Up a DNS Server"
date: 2008-05-13
forum: Server Platforms
---

### Post by saj0577 on 2008-05-13
On many websites for your DNS servers it ask you to type in a couple of different address:
dn1.dnswebsite.com
dn2.dnswebsite.com

Is it possible to do this so i can have it redirect to my home computer with a dns sever installed:
dns1.myipaddress
dns2.myipaddress


If so how would i go about setting up this dns sever?

The reason I wish to know is on my webserver i hope to set up a CPanel install just to make everything so much easier, as i have quite alot of domains too manage and if i a managing everything from my home server i might as well add my dns server too so the only thing i have to use other peoples services for is buying my domains and changing the nameservers.

Thanks in advance
Saj

---

### Post by lemming465 on 2008-05-19
> Is it possible to do this so i can have it redirect to my home computer with a dns sever installed:
dns1.myipaddress

Only if you get an official DNS delegation from your upstream provider.  It's usually a bad idea to try to do this to a home machine.  

On the other hand, having your home machine run a caching DNS server so you can get faster responses and control where it goes is quite a good idea. You can use something simple like *dnsmasq* or something complicated like *bind9* depending on your needs.

---

### Post by windependence on 2008-05-20
You don't have to use anyone's DNS servers in particular. You can try 2.2.2.4, 2.2.2.5, and 2.2.2.6. They are fairly fast servers right on the internet backbone. Running a DNS server locally is not necessary unless you have a large amount of computers (>10).

-Tim

---

