---
title: "DNS consolidation question"
date: 2010-08-07
forum: Server Platforms
---

### Post by handy-man on 2010-08-07
I currently have a couple of boxes all running their own DNS servers (BIND) and now due to some free time and reorganisation issues...
 
Can I just change the IP address for the ns1.nnn.net and ns2.nnn.net to the same ip's as ns1.yyy.net and ns2.yyy.net and ditch the nnn.net server?
 
Obviously I'd have to copy accross the content and set up the domains in the yyy box, but will that quick hack work (i.e. can I have more than one DNS server using the same IP address?
 
Thanks in advance
 
 
 
Handy

---

### Post by Bachstelze on 2010-08-07
A bit confusing... Here's how I understand things: you have two domains nnn.net and yyy.net. Each domain has two name servers, ns1 and ns2.  Are all those servers different physical machines?

---

### Post by handy-man on 2010-08-07
OK Sorry..
 
I have 2 servers both the namebased hosting a number of domains...
 
The domains on server 1 use the DNS ns1.xxx.net  ns2.xxx.net
The domains on server 2 use the DNS ns1.yyy.net  ns2.yyy.net
 
I want to merge the two servers...
 
So if I copy all the domain content across and set up each domain in BIND and all of that... Can I just go and change the IP's associated with:
ns1.xxx.net => the same IP's as ns1.yyy.net & 
ns2.xxx.net => the same IP's as ns2.yyy.net
 
Will that bring all the domain to the same box?
 
I know it should as the domain is just a 'human' way of looking at IP's
 
Does that make more sence?
 
A.

---

### Post by Bachstelze on 2010-08-07
Not really. What *are* all the ns* servers? Which of them are actual, physical machines, and which are just several names for the same machine?

---

### Post by gombadi on 2010-08-07
> 
(i.e. can I have more than one DNS server using the same IP address?


You can have one instance of bind listening on port 53 on an ip address. That one instance of bind can answer queries about many domains - we have one instance of bind running that answers questions for 100+ domains all working from the same ip address.

If you copy the domain files over to the new server and configure the new server(ns1 & ns2.yyy.net) to answer for the xxx.net domain, then log into your domain registrar and change the ip address for the nameservers for domain xxx.net to the same ip address as for yyy.net, wait a week and then shutdown bind on the old server(ns1 & ns2.xxx.net) it should all work.

The world will ask the root nameservers who handles queries for xxx.net and they will reply by saying the server that handles queries for xxx.net can be found at ip address a.b.c.d. which will be the ip address for ns1 & ns2.yyy.net

---

### Post by handy-man on 2010-08-08
Kool - Thanks, that's what I thought, It's just going to save me going through all the DNS settings on the domains (I will get to it, as I have to move them into a new account at my registerer, again to consolodate things - when I got them you had to use the default name for ownership, not they are more set up for resellers, and you can use different names (as owner) for each domain if you requre...)
 
I just have to get my 'shizzle' organised - So I can see what I have at a glance!
 
Thanks Guys you've been a Great help.
 
 
 
A.
 
PS just need to sort out some permissions now - then I'm all ready to rock!

---

