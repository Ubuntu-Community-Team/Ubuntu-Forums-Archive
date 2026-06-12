---
title: "Host a Currently 3rd party hosted Domain"
date: 2007-03-08
forum: Server Platforms
---

### Post by uamusa on 2007-03-08
I currently have a really "low traffic" domain being hosted with Yahoo.  I would like to begin hosting it from home using Ubuntu & Apache2.  I am currently able serve pages using my dynamic IP(I will be getting a static IP soon) address, but would like to be able to use the Domain name.  Could anyone tell me the steps necessary to do this?

Also, can I serve multiple domains from this server?  And if so, is bandwidth really my only "limiting factor" in doing so?

Thanks in advance - Chris

---

### Post by coxc24 on 2007-03-08
Do a search for DDNS (Dynamic DNS) and the posts should give you the answer. This will allow you to host a web site on your dynamic IP until your static one is available.

[http://www.dyndns.org](http://www.dyndns.org)
[http://www.no-ip.com](http://www.no-ip.com)

They are just 2 DDNS sites available for free use, there are many more.

---

### Post by Mr. C. on 2007-03-08
It's not clear to me from your posting who is the registrar for your domain; I presume Yahoo, but perhaps you only have pages there, and already own a domain.  If Yahoo is the owner of the name, then they would need to allow you to configure an "A" record that points to your server's IP.  They likely do not provide this for dynamic IPs. 

So, you need your own domain name, either via the services as coxc24 indicates, or via purchase through a registrar.  If you use a DDNs service, they will provide you with a list of domain names you may choose from, all under their control.  Purchasing your own means you can create things like anything.mydomain.com, where you choose the anything.  Of course, the mydomain.com must not be already owned.

Here are the steps:
1) purchase a domain name from a registrar (enom, godaddy, network solutions, etc.)
2) configure your domain via the registrar's tools, to "point" to your server's IP address (static only).

That's about it in a nut shell.
MrC

---

### Post by MJN on 2007-03-08
> **Mr. C. said:**
> 
2) configure your domain via the registrar's tools, to "point" to your server's IP address **(static only)**.

Not necessarilly - even if the registrar does not support dynamic updates you could always configure the domain as a CNAME to a dynamic-compatible domain where you can keep it updated to follow a dynamic IP. The end user (visitors) will be quite unaware of the interim lookup thus for all intents and purposes the domain would resolve directly to a dynamic IP address.

Mathew

---

### Post by Mr. C. on 2007-03-08
Yes, you are correct.  I figured we'd take baby steps.

The OP should be aware that this trick does not play well with running a mail server, and some configurations.

MrC

---

