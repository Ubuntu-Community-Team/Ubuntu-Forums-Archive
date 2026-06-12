---
title: "Bind Server w/o Static IP?"
date: 2008-03-12
forum: Server Platforms
---

### Post by oxsyn on 2008-03-12
Is it possible to run a BIND server (with a domain name) without having a static IP address?

---

### Post by MJN on 2008-03-12
Not really, as your parent domain needs to define who is authoritive for your domain. This is done by IP address and hence if yours changes you'd need to get this updated - this is usually a manual process with 'standard' domains (e.g. .com, .co.uk etc).
 
A workaround could be to delegate your domain in the parent namespace to some records which you could dynamically update, however this would not usually satisfy your registrar who usually require IP addresses, and not names, to be registered.
 
Mathew

---

### Post by wieman01 on 2008-03-12
Would DynDNS be an option? Just a thought, I really know nothing about BIND.

[http://www.dyndns.com/]("http://www.dyndns.com/")

I use it for my FTP server.

---

### Post by oxsyn on 2008-03-12
I'm currently using dynsdns ... but as far as I know, that doesn't work with bind.

---

