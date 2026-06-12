---
title: "GrSecurity, WiFi &amp; Root login."
date: 2009-09-08
forum: Security
---

### Post by phillw on 2009-09-08
Hi,

I '**think**' I have installed Grsecurity (It shows as a boot option & boots), using this:

[http://kernelsec.cr0.org/](http://kernelsec.cr0.org/)

I used Synaptic to get gradm2.
And it seems to be there :-)
I've done enough digging on the Grsecurity site and found the wiki pages.
[http://en.wikibooks.org/wiki/Grsecurity/The_Administration_Utility](http://en.wikibooks.org/wiki/Grsecurity/The_Administration_Utility)
to understand about Learning mode. A couple of questions :

[LIST=1]
[*]Can someone tell me how to turn on Wi-Fi when I boot into the Grsecurity kernal ?
[*]It seems I have to re-enable the root login to use gradm2 - is this true ? (Should be good for a laugh, as I have 'hardened' su and disabled root).
[/LIST]

**Full System Learning**

 To enable full system learning, run gradm as [root]("http://en.wikipedia.org/wiki/Superuser") with the following options:
 # gradm -F -L /etc/grsec/learning.logs
This will enable the [Role-based Access Control]("http://en.wikibooks.org/wiki/Grsecurity/The_RBAC_System") (RBAC) system and initiate full system learning. That is, gradm will monitor and log what your system does. The log can then be used to build a least privilege policy for your system.
 



Thanks,

Phill.

---

