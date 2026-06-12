---
title: "SSLv3 and TLSv1.0 required - what to do?"
date: 2016-06-16
forum: Ubuntu Application Development
---

### Post by jjalling on 2016-06-16
Hi,

I have an old home automation system installed in my house - it is a relatively popular system in denmark called IHC. The problem is that the controller only supports SSLv3 and TLSv1.0.
I'm currently developing an application for the system, so what can I do to add SSLv3, TLSv1.0 to my application - In Ubuntu 16.04 and forward, SSLv3 support is disabled in OpenSSL, so do you guys have any ideas?

Thanks in advance,

BR Jonas

---

### Post by TheFu on 2016-06-16
Welcome to the forums.

Both of those protocols are broken and shouldn´t be used where any security is needed.  The **only correct answer** is for the home automation system to provide TLSv1.2 libraries and use those. Older protocols (prior to TLS v1.2) have been known to have issues for long enough that every device should have patches available. Be certain that whatever you do allows:
a) replacing the current TLS libraries with updated versions.
b) allows new cyphers and prevents broken cyphers from being used.

I realize this isn´t likely the answer you hoped for. Sorry. The easy answer is a broken solution at this point.

---

