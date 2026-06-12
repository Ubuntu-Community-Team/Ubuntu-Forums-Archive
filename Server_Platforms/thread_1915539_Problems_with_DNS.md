---
title: "Problems with DNS"
date: 2012-01-26
forum: Server Platforms
---

### Post by miltonaguiar on 2012-01-26
Hi all,
I'm trying to install and configure a DNS server here in my network.
I have a domain registered: madeirawhalemuseum.org
I have a public address
I want to install here in my server a web page that responds to [www.madeirawhalemuseum.org](www.madeirawhalemuseum.org)
I have followed the guide that is here in forum but I'm a little confuse. When in the guide appears the address 192.168.0.1 I should put the private address of my server or I should put the public address?
When in the registers of  madeirawhalemuseum.org.db has www i should put the private address or the public?
Anyone can help me in this?

Best regards

---

### Post by SeijiSensei on 2012-01-26
If the machine has a public IP, and the [www.madeirawhalemuseum.org](www.madeirawhalemuseum.org) hostname is intended to point to it, then you need the public IP address.

Addresses in [RFC1918]("http://tools.ietf.org/html/rfc1918") "private" network blocks like 192.168.0.0/16 cannot be reached over the Internet.  Routers on the public Internet will not forward traffic with these addresses.  They're intended entirely for internal networks not exposed to the Internet.

---

