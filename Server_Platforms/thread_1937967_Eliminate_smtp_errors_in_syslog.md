---
title: "Eliminate smtp errors in syslog"
date: 2012-03-08
forum: Server Platforms
---

### Post by BobS0327 on 2012-03-08
I am running Zoneminder on Ubuntu 11.10 server.  When I check the syslog, I have the following error:

> starting delivery: protocol: smtp host: mail file: 1330862041.5450
smtp failed: connect failed
sending failed: host not foundHow can I elliminate these repeated error messages?

---

### Post by kevdog on 2012-03-08
smtp means outgoing mail.  Are you trying to send mail from a local source?

---

### Post by BobS0327 on 2012-03-08
> **kevdog said:**
> smtp means outgoing mail.  Are you trying to send mail from a local source?

Nope.  I'm not intentionally trying to send mail from a local source.  I believe I may have misconfigured Ubuntu server for outgoing mail when I installed it.  I have absolutely no need to send outgoing mail. Thus, I'd like to stop smtp on boot up.

---

### Post by BobS0327 on 2012-03-10
Finally found a solution to this problem by removing the null mailer package.  
sudo apt-get remove nullmailer.

It appears to be a package to test email capabilities when developing applications.

---

