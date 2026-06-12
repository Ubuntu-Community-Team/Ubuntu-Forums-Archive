---
title: "Firestarter Events"
date: 2011-02-20
forum: Security
---

### Post by ehderube on 2011-02-20
Hi,

I have an event that is red:

202.119.208.220 service SSH

I checked the IP it's from china.  Just wondering what I should do?  Firestarter states:

> Red
A possible attempt to access a non-public service. Firestarter suggests you should pay special attention to these entries. Note that this does not have to mean someone is attempting an intrusion, only you can be the judge of that.

---

### Post by DiSTORT3D on 2011-02-20
blacklist it :popcorn:

---

### Post by ehderube on 2011-02-20
How do you do that?

---

### Post by cariboo on 2011-02-21
I'd say just ignore it, it probably is someone trying to brute force access to ssh. If you use ssh with private/public keys you have nothing to worry about. I'd suggest not using firestarter to monitor connections because you have to run it as root to do so ,which could lead to a security problem, and the majority of attempted connection firestarter flags are non-events.

---

