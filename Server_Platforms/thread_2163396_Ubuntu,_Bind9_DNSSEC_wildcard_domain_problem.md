---
title: "Ubuntu, Bind9 DNSSEC wildcard domain problem"
date: 2013-07-18
forum: Server Platforms
---

### Post by gorgiouol on 2013-07-18
Hi,
i have problem with my DNS server (BIND 9.7.0-P1). I enabled DNSSEC validation with options: dnssec-enable yes; dnssec-validation yes;.
I have registered domain bonobo.cz and there is *.ucetnictvi.bonobo.cz with DNSSEC ON (from my ISP). Google DNS find domain uol.ucetnictvi.bonobo.cz, DNSSEC testing servers find it too, but on my server i cannot find it.

```
named[150]: error (no valid NSEC) resolving 'uol.ucetnictvi.bonobo.cz/A/IN': 164.138.27.146#53
named[150]: error (no valid NSEC) resolving 'uol.ucetnictvi.bonobo.cz/A/IN': 81.2.199.19#53
named[150]: error (no valid NSEC) resolving 'uol.ucetnictvi.bonobo.cz/A/IN': 46.28.104.67#53
named[150]: error (no valid NSEC) resolving 'uol.ucetnictvi.bonobo.cz/A/IN': 37.157.192.2#53

```

Problem is only on domains with wildcards (asterisk). When i create domain somethink.ucetnictvi.bonobo.cz, everythink is OK, but on *.ucetnictvi.bonobo.cz error.

Thanks for help

---

