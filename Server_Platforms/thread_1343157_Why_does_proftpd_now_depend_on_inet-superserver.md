---
title: "Why does proftpd now depend on inet-superserver?"
date: 2009-12-01
forum: Server Platforms
---

### Post by calr0x on 2009-12-01
You definitely do not need it to run proftpd.  Anyone know why Debian/Ubuntu require it?

---

### Post by cdenley on 2009-12-01
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=507311](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=507311)

---

### Post by calr0x on 2009-12-01
I found that as well, but doesn't that post correct the dependancy, rather than explain it?

Proftpd does not require a inetd at all.  That is what I have yet to learn..

Am I mistaken?

---

### Post by cdenley on 2009-12-01
> **calr0x said:**
> I found that as well, but doesn't that post correct the dependancy, rather than explain it?

Proftpd does not require a inetd at all.  That is what I have yet to learn..

Am I mistaken?

As explained in the bug report, the package's scripts do use update-inetd, and the package maintainer apparently made it a dependency rather than make all update-inetd commands conditional on the existence of inetd. Proftpd itself works fine without inetd, but the package install/purge would fail.

---

### Post by calr0x on 2009-12-01
Thank you so much for explaining it to me.. I did read that thread but not well enough!

---

