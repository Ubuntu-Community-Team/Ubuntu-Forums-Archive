---
title: "LVM Encryption Question"
date: 2009-07-01
forum: Security
---

### Post by cmcannady on 2009-07-01
Sorry if this is a stupid question, but I'm still learning a about Linux.  Basically, I've recently decided to completely and totally defect from Microsoft-land!

So here's my question.  Not withstanding the obvious importance of a good phase-phrase, what's the effective encryption bit-rate for LVM + encryption for Ubuntu 8.04 LTS?

Thank you for your help!  -CC

](*,)

---

### Post by u-slayer on 2009-07-01
Find out for yourself:

```
cryptsetup create test /dev/ram0
dd if=/dev/mapper/test bs=32K of=/dev/null
```

That's the max speed your encryption can run at. Depending on the exacting cipher and hash, I can do 120+ MB/s, so I am limited by the speed of my hard drive, not the encryption.

---

### Post by cmcannady on 2009-07-07
thank you u-slayer, i'll give that a try.

---

