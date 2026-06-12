---
title: "linking domain name to desktop apache webserver ??"
date: 2011-10-17
forum: Security
---

### Post by mushy365 on 2011-10-17
In my ubuntu system here i have apache web server running. I was wondering how hard it is to get a domain name and link it to my desktop computer. 

My main problem is my ip isnt static so it will change. 
What nameservers do i use? 
What do i need to do in general?

---

### Post by i.r.id10t on 2011-10-17
I'd get a dyndns account and use that domain name ...

---

### Post by bodhi.zazen on 2011-10-17
> **mushy365 said:**
> In my ubuntu system here i have apache web server running. I was wondering how hard it is to get a domain name and link it to my desktop computer. 

My main problem is my ip isnt static so it will change. 
What nameservers do i use? 
What do i need to do in general?

Depends on how often your ip changes and what your ip provider charges for a static ip.

Honestly, in general, it is most cost effective to purchase a VPS and use your home box for testing.

---

### Post by Lars Noodén on 2011-10-18
+1 for the VPS, they are quite affordable nowadays.

If you go the dynamic route instead, then you can have the dynamic DNS service handle the A name and then point your own C name at the A name.  That would give you your own domain name on a dynamic address.

---

