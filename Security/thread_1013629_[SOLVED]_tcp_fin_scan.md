---
title: "[SOLVED] tcp fin scan"
date: 2008-12-17
forum: Security
---

### Post by melojo on 2008-12-17
I am getting tcp fin scans on port 80 inbound and outbound.
I have a Belkin router.
The outbound is what concerns me, does this mean they have 
compromised my router?

---

### Post by x3roconf on 2008-12-17
It's very common to see portscans.. and your router is not compromised.
I'm sure. :)

---

### Post by gTinker on 2008-12-17
> **melojo said:**
> I am getting tcp fin scans on port 80 inbound and outbound.
I have a Belkin router.
The outbound is what concerns me, does this mean they have 
compromised my router?

A FIN scan is just a not very efficient way of identifing a port that has a service listening. If no service is listening at the port, the system will drop an error message. On the other hand, if a service is listening, the system will drop the incoming packet silently. So, silence probably indicates a service at the port. A closed port replies to a FIN with a RST, that's probably the outgoing you see as a listening port isn't supposed to reply.

---

### Post by melojo on 2008-12-17
Makes sense you guys thanks

---

