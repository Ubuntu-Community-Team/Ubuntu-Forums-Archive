---
title: "Missing AUTH at port 587 postfix server"
date: 2009-03-31
forum: Server Platforms
---

### Post by fusa on 2009-03-31
When I connect to my postfix mail server at port 587, I am missing the AUTH lines after connecting.  They do show at ports 25, 465.  What could be causing this, or is this normal?

netcat server.com 465:
250-server.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-AUTH CRAM-MD5 PLAIN DIGEST-MD5 LOGIN
250-AUTH=CRAM-MD5 PLAIN DIGEST-MD5 LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

netcat server.com 587:
250-server.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN


...Nevermind, think I found the problem, in master.cf I had:
submission inet n       -       -       -       -       smtpd
instbut should have had:
submission inet n       -       n       -       -       smtpd

---

