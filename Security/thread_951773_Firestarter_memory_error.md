---
title: "Firestarter memory error"
date: 2008-10-18
forum: Security
---

### Post by R.Bucky on 2008-10-18
I am running Ubuntu 7.10 with Firestarter. The problem is that Firestarter quits at random with the following response through terminal:
```
***MEMORY-ERROR***: firestarter[12166]: GSlice: assertion failed: sinfo->n_allocated > 0
Aborted (core dumped)
```

Any suggestions on fixing this issue?

Background: Currently running a LAMP server, Ubuntu 7.10

---

### Post by Loukisgr on 2008-10-19
please check your iptables and see if it is configured. If so then you don't have to worry about your security. On the other hand i don't know how to solve your problem. Mayby an reinstall in your firestarter will fix it.

To check your security: sudo iptables -L.

---

