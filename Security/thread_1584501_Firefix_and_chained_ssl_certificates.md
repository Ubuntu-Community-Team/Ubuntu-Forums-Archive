---
title: "Firefix and chained ssl certificates"
date: 2010-09-29
forum: Security
---

### Post by w2vy on 2010-09-29
My website gets a "unknown issuer" error when accessing it from my ubuntu box and firefox.

It works fine from firefox on windows.

I am assuming there are some basic chained ceritifcates missing from my ubuntu system. I am running 10.4

The site is [https://GotGrit.com]("https://GotGrit.com")

Issued by Starfield
```
[1]Authority Info Access
     Access Method=On-line Certificate Status Protocol (1.3.6.1.5.5.7.48.1)
     Alternative Name:
          URL=http://ocsp.starfieldtech.com/
[2]Authority Info Access
     Access Method=Certification Authority Issuer (1.3.6.1.5.5.7.48.2)
     Alternative Name:
          URL=http://certificates.starfieldtech.com/repository/sf_intermediate.crt

```

[https://certs.starfieldtech.com/anonymous/repository.seam]("https://certs.starfieldtech.com/anonymous/repository.seam")

Two questions:

How do I fix this?

How do we insure these changes get propagated to general users?
Why? Because it will stop users from visiting my website!
(No I am not panicing... if it effects me it effects others too)

tom

---

### Post by demosthene1 on 2010-09-29
I am glad you posted this problem. My feeble attempts at solving this haven't worked, such as switching to Chrome.

let's see if someone knows of a simple solution. It is annoying.

---

### Post by w2vy on 2010-10-16
I am not sure why, but it is working fine now...

---

