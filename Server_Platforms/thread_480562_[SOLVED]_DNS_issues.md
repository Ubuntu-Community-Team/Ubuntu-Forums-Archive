---
title: "[SOLVED] DNS issues"
date: 2007-06-21
forum: Server Platforms
---

### Post by vdawg on 2007-06-21
Hello everyone,

I did a quick search and apologize if this had been brought up before, but i simply don't know where else to ask.

I have a server domain.com which points to a particular ip.

Is it possible to have xxx.domain.com to point to a different ip from domain.com?

If yes, then what would the DNS record look like?

thanks!

---

### Post by pkarjala on 2007-06-21
Are you hosting the DNS services yourself?  Or is it being hosted by someone else?

---

### Post by vdawg on 2007-06-21
DNS hosted by someone else

---

### Post by Mr. C. on 2007-06-21
> **vdawg said:**
> 
Is it possible to have xxx.domain.com to point to a different ip from domain.com?

Absolutely; that's the entire point of the hierarchical DNS structure.  Consider the "." domain, ".com" domain, and "mydomain.com" domains - all have different authoritative zones of control.  An "xxx.mydomain.com" is no different.

You need an A record which provides the host name to IP translation.  An example (private IP space) DNS record would be:

   xxx.mydomain.com  IN A    192.168.0.2

Have a look at my DNS notes: [http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)

MrC

---

### Post by vdawg on 2007-08-26
> **Mr. C. said:**
> Absolutely; that's the entire point of the hierarchical DNS structure.  Consider the "." domain, ".com" domain, and "mydomain.com" domains - all have different authoritative zones of control.  An "xxx.mydomain.com" is no different.

You need an A record which provides the host name to IP translation.  An example (private IP space) DNS record would be:

   xxx.mydomain.com  IN A    192.168.0.2

Have a look at my DNS notes: [http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)

MrC

lol thanks we ended up figuring it out :)

---

