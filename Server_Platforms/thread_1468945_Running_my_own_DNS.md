---
title: "Running my own DNS"
date: 2010-05-01
forum: Server Platforms
---

### Post by Vegan on 2010-05-01
So at present my registrar has a DNS server, its not setup properly so I am thinking of leveraging the Linux box for that too.

I have BIND9 installed, and I have Webmin so I waneted soom suggestions to move the DNS master from the registrar's server to my own where I can create CNAME records as I want.

---

### Post by windependence on 2010-05-01
What do you mean by "not set up properly"?

-Tim

---

### Post by Vegan on 2010-05-01
When I use their web page to create a CNAME it crashes with an error. It also thinks the www alias is an A record when its really a CNAME.

---

### Post by Vegan on 2010-05-02
punt
:guitar:

---

### Post by windependence on 2010-05-03
> **Vegan said:**
> When I use their web page to create a CNAME it crashes with an error. It also thinks the www alias is an A record when its really a CNAME.
Sounds like you need to get in touch with their tech support, not run your own DNS.

It's almost never a good idea to run an authoritative DNS for your own site because you don't have the uptime and redundancy needed. I have redundant servers, power, and UPS and I STILL don't run my own DNS for a few reasons one of which is that it's a pain in the rear. Do yourself a favor and use your registrar's DNS services. Most times they are free with your domain name. Notice I said your REGISTRAR, NOT your ISP. That is the better way to go. If you don't like your registrar's services, transfer your domains to a good one.

-Tim

---

### Post by Vegan on 2010-05-04
I offered my services to fix their web page, no answer as of yet.

I am good with web development, and getting better at it every day it seems.

---

