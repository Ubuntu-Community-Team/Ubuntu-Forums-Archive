---
title: "Run A DNS Service Like ZoneEdit"
date: 2010-01-15
forum: Server Platforms
---

### Post by trentscott4 on 2010-01-15
I'm interested in setting up and providing my own DNS services for public use.  I have two separate server machines and can easily put an extra NIC card or two in any machine, if required.  What would it take to create such a service like ZoneEdit or EveryDNS?

I know I'd probably need to register 2+ static IP addresses thru Comcast and open a whole host of ports on my router.  How would I set this up in terms of software?  Is BIND the right tool for the job with a control panel in Usermin/Webmin?

Any recommendations, links or suggestions are greatly appreciated.

---

### Post by trentscott4 on 2010-01-17
Anyone?

---

### Post by Vince L on 2010-01-17
I'm with you,i been trying to code a panel to do this but didn't get far :(

---

### Post by trentscott4 on 2010-01-22
Anyone else with ideaS?

---

### Post by BobVila on 2010-01-22
Bind's the right way to go here, but the idea's a little wacky.

First, I'm not sure I'd want someone with a Comcast connection hosting my DNS records. Second, it's only a matter of time until you "accidentally" change an A record and everyone who goes to "myexampledomain.com" gets goatse'd.

If you're just out to learn how to configure/manage DNS, like I said initially, have fun with bind

---

