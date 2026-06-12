---
title: "Postfix over internet"
date: 2013-03-16
forum: Server Platforms
---

### Post by benj.545 on 2013-03-16
I am having an issue with my server where it is not accepting emails or connections over port 25 from the internet.  If I try to access port 25 on the localhost I am able to connect fine, and the same is with sending out, port 25 can send emails.  When on the LAN it is also possible to connect to the port.  I have had it set up to receive mail before although for what ever reason now it doesn't want to.  We haven't touched in the router settings and haven't messed with any other settings.

---

### Post by prodigy_ on 2013-03-16
> **benj.545 said:**
> not accepting emails or connections over port 25
Check with **telnet ip-address 25** from outside your network. If you get a timeout, then port 25 is either blocked (possibly by your ISP) or not forwarded properly. Or both.

---

