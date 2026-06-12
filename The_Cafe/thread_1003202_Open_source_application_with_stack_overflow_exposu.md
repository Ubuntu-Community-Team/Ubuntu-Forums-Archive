---
title: "Open source application with stack overflow exposure"
date: 2008-12-05
forum: The Cafe
---

### Post by screamingterror on 2008-12-05
Hi everyone,
Does anyone know of any applications on the web that have stack overflow vulnerabilities?  I'm learning IT security and need to be able to download an application on my local box and try to find the exposure.  I'm just having a hard time finding something out there...

Any guidance would be greatly appreciated.

Thanks in advance!

---

### Post by MaxIBoy on 2008-12-05
Open Source applications don't usually have known bugs, because they get fixed by people such as yourself.

Be a white-hat cracker. Get an old box set up as a server with an assortment of programs, ssh in every once in a while and try to gain root access. If you succeed, fix the bug and submit a patch.

You'll get experience, and the application developer will be grateful.

---

### Post by doas777 on 2008-12-05
check out the US-CERT for threat advisories. xine and xine-lib were noted as having numerous heap overflow vulnerabilities last week, but it's not web-facing.

good luck with your studies. that sounds like a really kewl lab!

---

