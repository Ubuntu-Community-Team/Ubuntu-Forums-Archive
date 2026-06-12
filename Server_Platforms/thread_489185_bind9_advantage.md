---
title: "bind9 advantage"
date: 2007-07-01
forum: Server Platforms
---

### Post by prostock3 on 2007-07-01
What is the advantage of having your own dns server?

Thanks.

---

### Post by Bachstelze on 2007-08-03
Moved to the Servers & Security forum.

---

### Post by koenn on 2007-08-03
> **prostock3 said:**
> What is the advantage of having your own dns server?

That, when you have your own network, there's a dns server to translate between host names and ip adresses on that network.

---

### Post by Mr. C. on 2007-08-04
[LIST]
[*]Fast, rich cache
[*]Complete control over your zones
[*]Far more power than any ISP/DNS provide yields
[/LIST]

MrC

---

### Post by murraymca on 2007-08-05
djbdns ([http://cr.yp.to/djbdns.html](http://cr.yp.to/djbdns.html)) might be a better option than bind.  

It's (in my opinion) more secure and easier (depends what you are use to) to add your own hosts - also you can't run cache+dns on the same server which will increase security (yes I know you can restrict recursive queries in bind...)

All the best.

---

