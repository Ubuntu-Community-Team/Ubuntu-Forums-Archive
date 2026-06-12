---
title: "Are those Clamavs updated?"
date: 2008-04-25
forum: The Cafe
---

### Post by sefs on 2008-04-25
The ClamAV antivirus scanner contains a vulnerability that may allow an attacker to execute code, or cause ClamAV to crash.

Full bulletin -> [http://www.kb.cert.org/vuls/id/858595](http://www.kb.cert.org/vuls/id/858595)

---

### Post by pot_roast on 2008-04-28
ClamAV seems to be one of those super important packages that gets left behind...

on a brand new Hardy installation..

ClamAV update process started at Mon Apr 28 20:03:29 2008
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.92.1 Recommended version: 0.93
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)


--

Easy to fix.. download the source and simply replace the binary, but still...

---

### Post by spacesamurai on 2008-04-29
This isn't the first time clamav has had a security hole. Orevious verisons had similar problems. Kinda makes you wonder if it is safe to install anyway, with viruses not being a real issue in Linux (until now at least) :)

The current engine is .93, but you will need to install it from the source. As far as I know, any clamav package contains the older engines, but from personal experience, clamav is safer by using the source to quickly update.

---

