---
title: "How to setup a nameserver, register a domain and point it to this nameserver?"
date: 2010-05-28
forum: Server Platforms
---

### Post by jabalsad on 2010-05-28
Hi guys,

I'm trying to setup a new nameserver using bind9 in ubuntu and host a  newly created domain on this nameserver.

I'm a bit confused in a chicken-and-egg kind of way. When I go to  godaddy.com and choose a new domain, they ask where I will be hosting  these domains. Since I want to host them on my (soon to be created)  nameserver, what domain names do I put in here? :/ It will probably be  of the form ns1.mynewdomain.com and ns2.mynewdomain.com. However, when I  insert these two hostnames, I get a message saying "All nameservers  must be unique".

Should I first go to my host and setup the cnames and subdomains for  ns1/ns2.mynewdomain.com? If so I'm a bit confused about what the zone file will look like... Say my hostname is currently something like xxx.computeaws.com, do I follow this guide ([https://help.ubuntu.com/10.04/serverguide/C/dns-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/dns-configuration.html)) but replace example.com with xxx.computeaws.com ?

What values should I use when registering at godaddy?

Appreciate the feedback, thanks

---

### Post by EvilTchnlgy on 2010-05-28
Yes, You need to add the cname records first so that the nameservers can be used. I usually use an external dns service (i use freedns.afraid.org personally) to get my nameservers setup and then once i have everything set accordingly I switch over to my own nameservers

---

### Post by jabalsad on 2010-05-28
Ah okay. I'll be using godaddy's nameservers and then play around until i have my own nameserver working. :)

---

### Post by Vegan on 2010-05-29
I use BIND9 and I have it setup as a basic DNS for my domains. Given I have limited registrar ability, I need the DNS to register and create a vhost for a client's web page.

---

