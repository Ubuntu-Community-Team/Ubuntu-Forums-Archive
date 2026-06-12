---
title: "Has bind9 been patched for AA-01265?"
date: 2015-12-01
forum: Security
---

### Post by jlc2010 on 2015-12-01
Hi,

We want to enable DNS RPZ on our name server, but we're concerned that AA-01265 (see [https://kb.isc.org/article/AA-01265/0](https://kb.isc.org/article/AA-01265/0)) has not been addressed.  I haven't been able to find any info on Launchpad if it has been patched.  Does anyone know & if so which version should we ensure is installed?

Thanks.

    -John

---

### Post by deadflowr on 2015-12-02
Same bug or different bug:
[http://www.ubuntu.com/usn/usn-2669-1/](http://www.ubuntu.com/usn/usn-2669-1/)
?

---

### Post by jlc2010 on 2015-12-02
I think that is a different bug, ISC reference # AA-01267.

---

### Post by QDR06VV9 on 2015-12-02
> **Solution:**[COLOR=#000000][FONT=Arial]  Upgrade to the patched release most closely related to your current version of [/FONT][/COLOR]BIND[COLOR=#000000][FONT=Arial]:[/FONT][/COLOR]
[LIST]
[*]BIND 9 version 9.9.7-P1
[*]BIND 9 version 9.10.2-P2
[/LIST]


From Here [https://kb.isc.org/article/AA-01267/0/CVE-2015-4620%3A-Specially-Constructed-Zone-Data-Can-Cause-a-Resolver-to-Crash-when-Validating.html](https://kb.isc.org/article/AA-01267/0/CVE-2015-4620%3A-Specially-Constructed-Zone-Data-Can-Cause-a-Resolver-to-Crash-when-Validating.html)
Regards

---

### Post by jlc2010 on 2015-12-02
I looked at the original AA-01265 notice more closely & saw that only the ISC BIND Subscription version 9.9.3 - 9.9.7 were affected.  They probably backported something from BIND 9.10 for their subscription customers.  So is it safe to assume that the Ubuntu version is not affected?

---

### Post by QDR06VV9 on 2015-12-02
Yeah that's how I read it also.
Redhat and BSD distro's were all that were referenced to.
Looks to  me like it was patched [COLOR=#000000][FONT=Verdana]**2015-07-08 16:53:12 CEST **[/FONT][/COLOR]

---

