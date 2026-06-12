---
title: "mail server - forwarding timing out"
date: 2006-05-07
forum: Server Platforms
---

### Post by Zelut on 2006-05-07
I'm running a small mail server and everything seems to be working (spamassassin, amavis, etc) except for email forwarding.  If I create an account that is set to forward to another it times out.  Here is some output from my mail.log:

postfix/qmgr[10656]: 98D7A240B5E: from=<my.email@domain.com>, size=1502, nrcpt=2 (queue active)
postfix/smtp[10829]: connect to 127.0.0.1[127.0.0.1]: Connection timed out (port 10024)
postfix/smtp[10829]: 98D7A240B5E: to=<recipient@aol.com>, relay=none, delay=30, status=deferred (connect to 127.0.0.1[127.0.0.1]: Connection timed out)
postfix/smtp[10829]: 98D7A240B5E: to=<my.email@domain.com>, relay=none, delay=30, status=deferred (connect to 127.0.0.1[127.0.0.1]: Connection timed out)
spamc[10817]: connect(AF_INET) to spamd at 127.0.0.1 failed, retrying (#2 of 3): Connection timed out

---

