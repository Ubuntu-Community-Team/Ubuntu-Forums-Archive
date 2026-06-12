---
title: "How to create subdomains that direct to another pc"
date: 2008-12-22
forum: Server Platforms
---

### Post by gased on 2008-12-22
Hi there

So i've got a domain name registered and a site hosted at apache server. I want to create subdomains. My hosting company gives me the opportunity to create subdomains through it's client area but can't handle to do it. So i want to create through my server that i believe its much much easier :)
I know that i have to do with virtualhosts but do not know what exactly to do. Via proxy or just this?
<VirtualHost *:*>
ServerName hostname.example.com
</VirtualHost> 

And how exactly could reverse could help me to do that??
Also do i have to install bind or dns from my hosting company is enough?

For example. The servers name is now ilion.awmn.com
i want this server to have my domain name as joy.hellug.gr
I have the domain hellug.gr and its pointing to server A (hellug.gr)
Please help me understand the differences between the one that my company offers and the one i can do with vhosts and apache. :)

Ty in advance and sorry for the long posting.

---

### Post by spiderbatdad on 2008-12-22
[http://www.yolinux.com/TUTORIALS/ApacheRedirect.html](http://www.yolinux.com/TUTORIALS/ApacheRedirect.html)

take a look at methods 5, 6, 7.

---

### Post by namdung on 2008-12-23
> **gased said:**
> Hi there

So i've got a domain name registered and a site hosted at apache server. I want to create subdomains. My hosting company gives me the opportunity to create subdomains through it's client area but can't handle to do it. So i want to create through my server that i believe its much much easier :)
I know that i have to do with virtualhosts but do not know what exactly to do. Via proxy or just this?
<VirtualHost *:*>
ServerName hostname.example.com
</VirtualHost> 

And how exactly could reverse could help me to do that??
Also do i have to install bind or dns from my hosting company is enough?

For example. The servers name is now ilion.awmn.com
i want this server to have my domain name as joy.hellug.gr
I have the domain hellug.gr and its pointing to server A (hellug.gr)
Please help me understand the differences between the one that my company offers and the one i can do with vhosts and apache. :)

Ty in advance and sorry for the long posting.

I've registered my domain with easydns.com which gives me the complete freedom to create as many subdomains pointing at different servers.

Similarly I've also created a local DNS entry which can have as many subdomains again pointing to different servers.

---

### Post by gased on 2008-12-23
Ok got it :D Ty guys :)


But in order to create reverse dns?

---

### Post by hyper_ch on 2008-12-23
the simplest would be to alter the dns zone file for that domain and have the subdomain point to another IP/(dynamic)domain

---

