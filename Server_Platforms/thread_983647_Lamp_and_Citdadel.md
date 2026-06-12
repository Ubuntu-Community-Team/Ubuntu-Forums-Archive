---
title: "Lamp and Citdadel"
date: 2008-11-15
forum: Server Platforms
---

### Post by quikone8 on 2008-11-15
How would someone go about running servers side by side on one machine?  I have a Citadel mail server running on 8.10, is it possible to  LAMP on the same machine?  If so , how?  It seems as if Citadel and LAMP want to run on Localhost/127.0.0.1, do they just get assigned different ports?  Are there any forums or wikis  to explain how to do the above?:confused:

---

### Post by devonps on 2008-11-16
> **quikone8 said:**
> How would someone go about running servers side by side on one machine?  I have a Citadel mail server running on 8.10, is it possible to  LAMP on the same machine?  If so , how?  It seems as if Citadel and LAMP want to run on Localhost/127.0.0.1, do they just get assigned different ports?  Are there any forums or wikis  to explain how to do the above?:confused:

First - I don't think you can run anything else on a Citadel server.

Second - I wouldn't place both those types of servers on the same physical machine, for security reasons. If one gets hacked the 2nd one would fall pretty quickly.

Third - If the web server gets hit by a DDoS attack then that will also grind into your email server.

Fourth - even if you did manage to avoid the above issues you would then have an issue of networking and port-forwarding!

I've assumed LAMP = web server for you.

I'd recommend seperating them onto 2 physical machines.

Steve.

---

### Post by Thirtysixway on 2008-11-16
You could use your server to run 2 virtual machines, one for web and one for email.

---

