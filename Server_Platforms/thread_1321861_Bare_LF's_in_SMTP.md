---
title: "Bare LF's in SMTP"
date: 2009-11-10
forum: Server Platforms
---

### Post by Gorlist on 2009-11-10
Good day, just had a phone call this evening from someone who use's a hosting account on our server - and mentioned Outlook express is popping up with an error, and timesouts.

Ive not seen the error myself (going to pop around and check it tomorrow morning), however in the logs for that account im noticing: 

```
Nov 10 16:39:32 sv1 qmail-local-handlers[9962]: mailbox: /var/qmail/mailnames/my-domain.co.uk/meg
Nov 10 16:46:44 sv1 qmail-queue-handlers[10036]: possibly qmail-smtpd exited by timeout, reset connection. ^I^I^I^ISee "http://pobox.com/~djb/docs/smtplf.html." for get more information.
Nov 10 16:46:49 sv1 qmail-queue-handlers[10041]: possibly qmail-smtpd exited by timeout, reset connection. ^I^I^I^ISee "http://pobox.com/~djb/docs/smtplf.html." for get more information.
Nov 10 16:46:59 sv1 pop3d: 1257871619.663804 DISCONNECTED, user=meg@my-domain.co.uk, ip=[43.123.841.246], top=0, retr=263787, time=485, rcvd=258, sent=269885, maildir=/var/qmail/mailna$
Nov 10 17:27:50 sv1 pop3d: 1257874070.580533 TIMEOUT, user=meg@my-domain.co.uk, ip=[43.123.841.246], top=0, retr=227668, time=666, rcvd=162, sent=232382, maildir=/var/qmail/mailnames/r$

```

(note ive changed the email address, domain and ip).

Ive checked out the suggested URL, and read through the rather sparse page, done a search but it appears to be a giant topic that dates back a number of years.

It only effects this one particular email address, so im at a lost to explain, or even go about fixing?

So is the error qmail, or outlook express in this case?

Any suggestions?


Ubuntu 8.04 LTS, running Plesk 9.2.3. 
Error: Timeout, [http://cr.yp.to/docs/smtplf.html](http://cr.yp.to/docs/smtplf.html)

---

