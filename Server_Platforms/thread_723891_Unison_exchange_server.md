---
title: "Unison exchange server"
date: 2008-03-14
forum: Server Platforms
---

### Post by mhdagley on 2008-03-14
So I am trying to install the server on my system to see if it will work for the company I work for. Anyways it asks for a full qualified domain name. What do I put here? Nothing I have tried has worked. 



Thanks in advance,



M

---

### Post by rickyjones on 2008-03-14
> **mhdagley said:**
> So I am trying to install the server on my system to see if it will work for the company I work for. Anyways it asks for a full qualified domain name. What do I put here? Nothing I have tried has worked. 



Thanks in advance,



M

I have never worked with that software but if it is asking for the domain name then you'll have to provide it. Have you assigned one to your server? Is this an internet facing server that you purchased a domain name for?

If it for internal use only then you can just make one up. Just remember to assign it to the computer by editing the /etc/hosts and /etc/hostname files.

An example for an internal domain name that I like to use is: solarsystem.local

In that example the FQDN of my server would be: server.solarsystem.local

If you purchased an actual domain for this server then use that domain. Ex: server.realdomain.com

I hope this helps!

-Richard

---

### Post by mhdagley on 2008-03-14
Thats what I thought. It is giving me trouble on entering it. Thanks for the help!

---

