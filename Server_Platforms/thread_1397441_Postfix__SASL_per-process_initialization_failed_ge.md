---
title: "Postfix:  SASL per-process initialization failed: generic failure"
date: 2010-02-03
forum: Server Platforms
---

### Post by rterio on 2010-02-03
Hi,

I instaled an imap mail server on Ubuntu 8.04 server with Postfix2.5.1/Cyrus2.2

We use a web mail application for schools called Edugroupe and everything work fine (receive and send email OK).  But when we try to use a mail client (Thinderbird or Outlook) we are unable to send email.  Here is the error message from mail.log:

> Feb  3 09:34:21 mail postfix/smtpd[9912]: warning: SASL per-process initialization failed: generic failure
Feb  3 09:34:21 mail postfix/smtpd[9912]: fatal: SASL per-process initialization failed
Feb  3 09:34:22 mail postfix/master[9881]: warning: process /usr/lib/postfix/smtpd pid 9912 exit status 1
Feb  3 09:34:22 mail postfix/master[9881]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Feb  3 09:34:40 mail cyrus/master[4043]: process 9910 exited, status 0
Feb  3 09:34:41 mail postfix/master[9881]: terminating on signal 15
I searched about all thoses errors on Google, tried avout everything proposed and nothing worked...

I attach my postconf and configs files.

Thanks for your help!

---

