---
title: "segfault in console-kit-dae"
date: 2009-01-11
forum: Security
---

### Post by toto2k on 2009-01-11
Hi all,

First of all, I hope that this post is in the right place.

So I have found this in my logs :

[3698436.303960] console-kit-dae[25959]: segfault at 44 ip b7fa158c sp b7ba6320 error 4 in libglib-2.0.so.0.1800.2[b7f75000+b5000]

What does it mean ?

Thanks

---

### Post by The Tronyx on 2009-01-11
That error says to me that the program crashed due to a segmentation fault.  This generally happens when an application tries to access memory that has not been allocated to it or that it does not have access to.

If you asking with regard to a security issue, segfaults can indicate security breaches however if this is a desktop used at home, I highly doubt someone is attempting to force console-kit-dae into a denial of service state or attempting some kind of stack/heap overflow exploit.

I guess to put it simply, that error means that application or one of its components is crashing.

---

### Post by adamlau on 2009-01-11
YMMV, but I have found that reinstalling the offending application oftentimes resolves segfault conditions.

---

### Post by toto2k on 2009-01-14
Thanks for your reply.

I have found this error in my log and it repeats every four/five days. So I think the application is crashing and it's not a security issue.

---

### Post by james.walmsley on 2009-02-06
Come on guys, you should be reporting this to Ubuntu as a bug!

Its happened to me too, so I will file a bug report with Ubuntu. Seg-faults should never happen in a perfect system, so if you see them try to explain the condition of how it happens, and report to the developers to get it fixed.

Who knows what you could do with this, maybe nothing, but maybe it could be exploited.

All the best, and happy linuxing!

James

---

### Post by martin_lindhe on 2009-04-14
here is the relevant bug in launchpad:

[https://bugs.launchpad.net/bugs/196724](https://bugs.launchpad.net/bugs/196724)

---

