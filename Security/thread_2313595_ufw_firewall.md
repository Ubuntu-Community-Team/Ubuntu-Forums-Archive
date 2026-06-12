---
title: "ufw firewall"
date: 2016-02-13
forum: Security
---

### Post by neil37 on 2016-02-13
Hi,

I'm new'ish to Linux and recently enabled UFW on Ubuntu 14.04.
When I enabled the firewall it seemed to block all ports by default?
If this is the case does it apply to both outgoing traffic or just incoming?

And to set a rule to deny a port (sudo ufw deny port <port number>). What would this benefit?

---

### Post by deadflowr on 2016-02-14
Moved to Security sub-forums

By default, when enabled, ufw denies all incoming, but allows all outgoing.

---

### Post by neil37 on 2016-02-14
> **deadflowr said:**
> Moved to Security sub-forums

By default, when enabled, ufw denies all incoming, but allows all outgoing.

Thank you :D That helped allot.
And that is good to know.

---

