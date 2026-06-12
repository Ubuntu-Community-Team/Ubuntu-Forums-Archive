---
title: "Periodic + Cron"
date: 2007-04-30
forum: Server Platforms
---

### Post by drinehart on 2007-04-30
The company where I work has a hosted web page on a FreeBSD server.  I receive e-mails from the root user about security and such and wanted to replicate that on the in-house ubuntu server we have.  I believe the package is called periodic but am not sure.  The e-mails I receive have subject lines like "daily run output" or "security run output".

The scripts on the FreeBSD server were located in /etc/periodic

The daily report tells me the disk status (free space), tells me about the mail queue or if any mails hosts were rejected.

The security report tells me how many users have UID of 0 and about login failures.

Does anyone know if this package or equivalent is available for ubuntu?

Duane

---

### Post by elst on 2007-05-01
I use "logwatch" on my servers, which is fairly standard and WFM, but there are probably other packages in the repositories that also do this, too. It's a good idea to install Postfix yourself before you add a log analyzer, as otherwise the installation will try to resolve the package dependency on a mail service as best it can.

---

