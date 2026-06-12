---
title: "Mozilla Firefox Transport Layer Security"
date: 2016-07-30
forum: Security
---

### Post by loungehake on 2016-07-30
I tested the Ubuntu implementation of Firefox using [https://www.ssllabs.com/](https://www.ssllabs.com/) and found to my dismay that Ubuntu Firefox allows SSL3.  There seems to be no way to prevent the use of SSL3.  I want to ensure that ONLY TLS1, TLS1.1 and TLS1.2 are permitted.

The Version of Firefox which runs on Microsoft Windows only allows TLS so why does the Ubuntu version allow the unsafe SSL3?

I know that SSL 3.0 will happen only if the server agrees but my very modest understanding of the security of encrypted data causes me to be worried.

---

### Post by &amp;KyT$0P# on 2016-07-30
What version of Firefox are you using on Ubuntu?
What have you tried to do to prevent SSL 3 from being used?

---

### Post by yoshii on 2016-07-30
I ithought that thos TLS's that you mentioned were older than SSL3?  Maybe I'm wrong about this.  I thought it was better to disable the older protocols.

---

### Post by &amp;KyT$0P# on 2016-07-30
> **yoshii said:**
> I ithought that thos TLS's that you mentioned were older than SSL3?  
Nope, basically TLS is the next versions of SSL but they gave it a new name - [https://en.wikipedia.org/wiki/Transport_Layer_Security]("https://en.wikipedia.org/wiki/Transport_Layer_Security")

> I thought it was better to disable the older protocols.
It is.  SSL 3 is the older protocol.  In Firefox I don't think it's possible to disable a newer protocol without disabling older protocols.

---

