---
title: "Amavis Spamassassin logging?"
date: 2008-07-10
forum: Server Platforms
---

### Post by PraysToPan on 2008-07-10
Hi all,

I've poked around for hours and can't seem to find the right way to get Amavisd-new to log Spamassassin info to syslog.  Has anyone managed this with a near default setup of amavis on Hardy?

The main reason is bayesian autolearning doesn't seem to be working on my setup.

Thanks,
Jon

---

### Post by PraysToPan on 2008-07-13
Bayes is working fine.  It appears Amavis isn't providing the autoleearn= header on marked up mail.

---

