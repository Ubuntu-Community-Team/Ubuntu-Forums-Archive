---
title: "heirloom-mailx vs mailutils"
date: 2011-01-27
forum: Server Platforms
---

### Post by jason0 on 2011-01-27
Hi,

Can anyone tell me what the pros and cons are between heirloom-mailx vs mailutils?  This is for ubuntu 10.04 LTS.  AT this point my only purpose is to use the mail command line program to occasionally send log output to email aliases.

--jason

---

### Post by kgatan on 2011-01-30
You need heirloom-mailx if you want to attach files to the mails, ie log files.

---

### Post by SeijiSensei on 2011-01-30
Depends on how you construct the message, doesn't it?  I can build a [MIME-encoded multipart message]("http://www.faqs.org/rfcs/rfc2045.html") manually then send it through any command-line mail client.  It's not easy to do, but not impossible either.  You just need to use the right headers to define the parts.

---

