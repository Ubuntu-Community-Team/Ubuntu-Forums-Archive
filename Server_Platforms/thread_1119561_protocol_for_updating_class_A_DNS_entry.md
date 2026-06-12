---
title: "protocol for updating class A DNS entry"
date: 2009-04-08
forum: Server Platforms
---

### Post by kevinfishburne on 2009-04-08
In the next few weeks I plan on moving from Bluehost to a Comcast Business line so I can have more control over my web site and mail addresses. I have a nice quad-core 8.04 server set up and it's ready to accept mail connections via exim, dovecot and Devil-Linux routing. Apache is running extremely quickly and the site looks great.

My Bluehost plan, which I may let expire for testing purposes, included domain registration with "FAST-12785240" or "FastDomain Inc." Is it possible to obtain control of the IP address assigned by DNS servers and continue to use FastDomain [f]or a legitimate domain registrar?

Any registrar will do, but I need control over the IP address assigned to my domain name.

---

### Post by BkkBonanza on 2009-04-08
I don't know anything about FastDomain in particular. You can likely just log into nyour account there and do any changes directly in a few minutes.

If you own the names (and they're in your name) then you can do what you want with them. If the registrar or DNS control you currently have isn't good then it should be a simple matter to transfer them to another. I've done it many times. It seems each registrar has there own quirks, but for me the general steps were: 1. ask my registrar for a transfer authorization code, 2. go to the new registrar and enter the code and name to transfer, pay money, 3. wait for various confirmation emails and confirm them. Usually took a few days or so to complete. 

If you want a good registrar with a decent control panel then I can recommend name.com - there are many others though. I've used this one for a couple years and never had any trouble managing my names and dns. Cheap price but also very functional full dns controls.

---

### Post by kevinfishburne on 2009-04-08
Awesome, thank you. It turns out that FastDomain doesn't offer "standalone" DNS registration and requires that you pay for web hosting services, etc. as well. I'm going to use either register.com or name.com as they appear to offer DNS registration only.

My plan at this point is to register a new domain name with my new registrar, which I will use for testing web and email on my server. Once I'm sure it's working then I'll transfer my domain name from my old registrar (Bluehost) to the new registrar, then update its IP address to point to my router here.

If that's not the proper way to do it please let me know. I'm trying to avoid as much down time as possible (of course). Thanks again for the info.

---

