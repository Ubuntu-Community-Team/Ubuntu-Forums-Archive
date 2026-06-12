---
title: "Vanity nameservers"
date: 2016-07-06
forum: The Cafe
---

### Post by SchnappiJedi on 2016-07-06
Hi,

Instead of actually creating one's own BIND or DjbDNS nameserver couldn't someone just host DNS with their registrar (or any other DNS service) and register/ create glue records such as ns1.vanitydomain.com pointing to the IP's of a registrars nameservers?

Does anyone do this?

---

### Post by TheFu on 2016-07-06
Yes. This is done all the time.

Registrar and DNS are 2 different, but connected, services.

The registrar maintains a record of the domain name and the authoritative DNS(es) for that domain. Nothing more .... well, besides billing and other extra crap for the business side of this stuff. 1st and 2nd level domain names are provided to the root DNS servers for the entire internet. Registrars often do not run DNS, though many do. 

If you don't have a DNS setup, then the registrar won't know where to point at.  Of course, those DNS services are available both stand alone or as packages with hosting or without it AND with DNS or without it AND with all 3 parts combined.

I haven't run my own public-facing DNS in about 15 yrs now.  DNS is one of the most often hacked services ... and I was hacked through it years ago.  Now I pay no-ip and dyn for DNS services.  $20 a year is relatively cheap insurance for my money.  Plus with dyn, I'm grandfathered for a few personal domains, so haven't paid a dime to them since the 1990s.  Actually, I sorta feel guilty about the dyn stuff and try to use them for commercial services whenever I can. They are hassle free, cheap and provide excellent value for my needs.

But ... some home router makers have also gotten into this business and include vanity subdomains for free with the price of a new router.  I'm positive netgear does this - ran into a client using it (though I'm not a fan of any home routers - too hard to keep them patched after 2 yrs).

Just look for "DNS services" to find some choices.

---

### Post by SchnappiJedi on 2016-07-08
Thanks. But I think you might have misunderstood. Meant create an A record ns1.yourdomain.com pointing to a large DNS server and use this as one's nameserver.

---

