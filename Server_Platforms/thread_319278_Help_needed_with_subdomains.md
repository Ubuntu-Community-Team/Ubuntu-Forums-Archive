---
title: "Help needed with subdomains"
date: 2006-12-15
forum: Server Platforms
---

### Post by timhaughton on 2006-12-15
Hi, I need a bit of help.

I run an ubuntu server at home, on a static IP (behind a router if that matters).

It is a LAMP server with MoinMoin (amongst other things) running on it.

I've registered a domain, (agibuntu.com) to be a home for resources about doing agile software development with opensource tools. I want to set up subdomains to access the different parts of the system.

[www.agibuntu.com](www.agibuntu.com) ==> General web site.
wiki.agibuntu.com ==> MoinMoin wiki.

Can anyone give me any pointers?

I've had agibuntu.com point at my home IP, and that seems to work fine. I've added wiki.agibuntu.com to also point to my home IP.

I can't seem to get MoinMoin working at all, even after following [the guide]("https://wiki.ubuntu.com/HelpOnInstalling").

Cheers,

Tim

---

### Post by chrisfay on 2006-12-15
You need to add a virtual host for the new subdomain in Apache's sites-available or sites-enabled.  Otherwise, how would Apache know where to send the request?

---

