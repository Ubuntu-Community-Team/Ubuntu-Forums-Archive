---
title: "Can't get preseed file: questions.dat missing (Jaunty)"
date: 2009-05-13
forum: Server Platforms
---

### Post by Joshua Swink on 2009-05-13
I would like to use preseeding in order to automate installations using Jaunty. However, I can't use debconf to generate the preseed.cfg file because questions.dat is missing.

I'm using the (old) guide here:

[https://help.ubuntu.com/7.04/installation-guide/i386/preseed-creating.html](https://help.ubuntu.com/7.04/installation-guide/i386/preseed-creating.html)

[FONT="Courier New"][INDENT]# debconf-get-selections --installer > preseed.cfg
debconf: DbDriver "di_questions": could not open /var/log/installer/cdebconf/questions.dat[/INDENT][/FONT]

Back in 8.10, this works. But not in Jaunty.

Is there any advice for generating a preseed file based on a Jaunty install, now that debconf-get-selections isn't working?

---

### Post by Joshua Swink on 2009-05-13
Note: the correct documentation ([https://help.ubuntu.com/9.04/installation-guide/powerpc/preseed-creating.html](https://help.ubuntu.com/9.04/installation-guide/powerpc/preseed-creating.html)) also advises using "debconf-get-selections --installer", so this isn't a problem caused by reading obsolete documentation.

---

### Post by MatsK on 2009-06-19
I can confirm this issue !

/M

---

### Post by guvnr on 2010-05-05
try this:-

debconf-get-selections > debconf
nano debconf

---

