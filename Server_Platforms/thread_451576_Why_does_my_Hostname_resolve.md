---
title: "Why does my Hostname resolve?"
date: 2007-05-22
forum: Server Platforms
---

### Post by blazercist on 2007-05-22
I host a website, well I'm trying at least.  This is probably a stupid question coming from a guy like me who knows most of this junk, but for some reason when I type my hostname into a browser "http://mywebsite.com"  it automatically resolves in the browsers address bar to my ip "http://xx.xx.xx.xx"  and I find it rather ugly and wanted to know how i could stop that from happening.  

I should mention that I have a "semi-static ip"  its cable broadband and the ip changes maybe once a year, but I've setup a dynamic dns account with DynDNS.org and my cable company game me 1 free domain, so it looks like this, my domain forwards to DynDNS which forwards to my ip.

Any help is greatly appreciated.

---

### Post by MrHorus on 2007-05-22
> **blazercist said:**
> 
I should mention that I have a "semi-static ip"  its cable broadband and the ip changes maybe once a year, but I've setup a dynamic dns account with DynDNS.org and my cable company game me 1 free domain, so it looks like this, my domain forwards to DynDNS which forwards to my ip.

Any help is greatly appreciated.

If memory serves then that's exactly how they operate and why it happens.

---

### Post by blazercist on 2007-05-22
Yea I kinda figured but, was wondering if there was a way around it.

edit: ok you can forget the DynDNS part of the equation, i forgot that I turned that off so its just my cable company forwarding from the hostname to my ip.

---

### Post by killerdragon on 2007-05-23
> **blazercist said:**
> Yea I kinda figured but, was wondering if there was a way around it.

edit: ok you can forget the DynDNS part of the equation, i forgot that I turned that off so its just my cable company forwarding from the hostname to my ip.

If your ISP is a good ISP ask them if they are willing to change NS records for you...then I would use a service like zoneedit.com or freedns.afraid.org .
You will get more control over the domain than just an A record. But, hey thats just my 2 cents.

---

