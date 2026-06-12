---
title: "why do some websites require you to type www?"
date: 2010-09-06
forum: The Cafe
---

### Post by user1397 on 2010-09-06
And others dont?

---

### Post by kevin11951 on 2010-09-06
Dns

---

### Post by murderslastcrow on 2010-09-06
Because they suck horribly. D:<

---

### Post by sandyd on 2010-09-06
> **murderslastcrow said:**
> Because they suck horribly. D:<
they haven't set their DNS properly.

It is kind of a terminology thing anyways.
WWW stands for world wide web, and theirs simply some people who want to get technical, and require the use of www on their sites....

---

### Post by YuiDaoren on 2010-09-06
There are domains that don't re-direct or resolve to the web server?

Weird.

No idea why anyone would do that. Seems pointless to make extra work for their customers.

---

### Post by nilarimogard on 2010-09-07
Some have no idea how to redirect their www to domain.com or the other way around :D

---

### Post by Joeb454 on 2010-09-07
> **nilarimogard said:**
> Some have no idea how to redirect their www to domain.com or the other way around :D

Then there's some - like this very forum - which automatically strip out the "www."

---

### Post by lz1dsb on 2010-09-07
I also think that it's all about DNS record for a particular site. Here's how it looks for a site that have www added to the DNS record:

~$ nslookup
> dir.bg
Server:		212.50.10.50
Address:	212.50.10.50#53

Non-authoritative answer:
Name:	dir.bg
Address: 194.145.63.12
> [www.dir.bg](www.dir.bg)
Server:		212.50.10.50
Address:	212.50.10.50#53

Non-authoritative answer:
[www.dir.bg](www.dir.bg)	canonical name = dir.bg.
Name:	dir.bg
Address: 194.145.63.12

Cheers, 
Boyan

---

### Post by Spice Weasel on 2010-09-07
The www is pointless. It's just easier for people who are computer illiterate to type "www.ubuntu.com" rather than "http://ubuntu.com". For some reason.

---

### Post by Spr0k3t on 2010-09-07
I believe the moniker www was officially deprecated in 1999 with the transitional html 3.2.  The correct method to handle the now defunct www is to remove the subdomain completely and redirect to the domain.

---

### Post by MechaMechanism on 2010-09-07
> **Spr0k3t said:**
> I believe the moniker www was officially deprecated in 1999 with the transitional html 3.2.  The correct method to handle the now defunct www is to remove the subdomain completely and redirect to the domain.
Yep, nothing dates a site like the www.

---

### Post by koenn on 2010-09-07
in "www.example.com", example.com is a domain name and refers to a name space; 'www' is an actual hostname, so [www.example.com](www.example.com) uniqly defines a host - a server, or, in the case of webserver virtual hosts, a website. So the www is an essential part of the URI.

Allowing a domain name (without the host part, so example.com) to resolve to a host ([www.example.com](www.example.com)) is, at best, a sane default, assuming that the most popular server in the domain is the web server. It kinda ignores the fact that the domain will at least also have name servers (often ns.example.com), and most likely mail servers, and some others (ftp.example.com, downloads.example.com, ...).



At some point, it became common to name (or at least alias) webservers 'www', but they might as wel be called 'server17' or 'john'. 

So, contrary to what someone posted before, it's probably the more computer literate people, who understand URIs and DNS, or gained there internet experience in the 90s, whe tend to use [www.example.org](www.example.org) i.s.o. example.org in web addresses


Although it may be so that the practice of defaulting a domain to its webserver is now a recommended practice - maybe I missed that meeting. 


> **Spr0k3t said:**
> I believe the moniker www was officially deprecated in 1999 with the transitional html 3.2.  The correct method to handle the now defunct www is to remove the subdomain completely and redirect to the domain.
I doubt that a language specification for text file markup would prescribe the recommended network configuration, hostname, and name resolution mechanism for the host where those text files are stored. 
But I could be wrong. 
Any references ?

---

### Post by spjackson on 2010-09-07
> **Spr0k3t said:**
> I believe the moniker www was officially deprecated in 1999 with the transitional html 3.2.  The correct method to handle the now defunct www is to remove the subdomain completely and redirect to the domain.
I note that w3.org does not appear to be aware of this: it redirects to [www.w3.org]("http://www.w3.org").

---

### Post by Dr. C on 2010-09-08
> **Spr0k3t said:**
> I believe the moniker www was officially deprecated in 1999 with the transitional html 3.2.  The correct method to handle the now defunct www is to remove the subdomain completely and redirect to the domain.

Is there a RFC or other reference for this or just a movement to get rid of the www. Interesting ubuntu.com does it one way and ubuntuforums.org does it the other.

---

