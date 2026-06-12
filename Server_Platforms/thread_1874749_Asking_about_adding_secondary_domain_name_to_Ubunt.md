---
title: "Asking about adding secondary domain name to Ubuntu server."
date: 2011-11-03
forum: Server Platforms
---

### Post by hieplc on 2011-11-03
Can somebody can help me with this problem:

I have an ubuntu server with global IP address: X.X.X.X

I have 1 domain name: myfirstdomain.com 

My first domain works very well, right now, I bought a new domain : myseconddomain.com, I created a folder on my ubuntu server X.X.X.X/newforlder, and I want to map my new domain to this folder, can I do that.

**Right now the IP X.X.X.X is mapped to the first domain.

this is my named.conf.local file:

zone "myfirstdomain.com:{
type master;
file "/etc/bind/zones/myfirstdomain.com.db"

Please give me an idea for this, I just want to use 2 domains in my Ubuntu server (different folder).

Thank you in advance

---

### Post by lisati on 2011-11-03
*Thread moved to **Server Platforms**.*
You might want to research **virtual hosts** - apache is able to cope with requests for different domain names and direct the requests to different websites.

---

### Post by hieplc on 2011-11-04
Hi lisati,
 
thank you for your reply, I am trying to do this way, hope it works

---

