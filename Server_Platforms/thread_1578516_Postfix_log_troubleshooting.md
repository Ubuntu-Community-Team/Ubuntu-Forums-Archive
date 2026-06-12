---
title: "Postfix log troubleshooting"
date: 2010-09-20
forum: Server Platforms
---

### Post by wesg on 2010-09-20
My LAMP server is not sending email to external addresses, and I can't figure out why. Below are the lines from /var/log/mail.log about the test email I sent. Can anyone find anything that might be the culprit?

I should mention I'm trying to redirect inbound mail to external addresses (Gmail, etc.)

```
Sep 20 14:34:33 server1 postfix/smtpd[1066]: connect from mail-wy0-f180.google.com[74.125.82.180]
Sep 20 14:34:33 server1 postfix/smtpd[1066]: C724C104301: client=mail-wy0-f180.google.com[74.125.82.180]
Sep 20 14:34:34 server1 postfix/cleanup[1071]: C724C104301: message-id=<657CFA3C-9922-49E3-A073-CC745E526F1E@gmail.com>
Sep 20 14:34:34 server1 postfix/qmgr[1065]: C724C104301: from=<inbound@gmail.com>, size=1987, nrcpt=1 (queue active)
Sep 20 14:34:34 server1 postfix/cleanup[1071]: 134DD104307: message-id=<657CFA3C-9922-49E3-A073-CC745E526F1E@gmail.com>
Sep 20 14:34:34 server1 postfix/local[1072]: C724C104301: to=<localuser@domain.com>, relay=local, delay=0.68, delays=0.66/0.01/0/0.01, dsn=2.0.0, status=sent (forwarded as 134DD104307)
Sep 20 14:34:34 server1 postfix/qmgr[1065]: 134DD104307: from=<inbound@gmail.com>, size=2118, nrcpt=1 (queue active)
Sep 20 14:34:34 server1 postfix/qmgr[1065]: C724C104301: removed
Sep 20 14:34:36 server1 postfix/smtp[1073]: 134DD104307: to=<outbound@gmail.com>, orig_to=<localuser@domain.com>, relay=gmail-smtp-in.l.google.com[74.125.113.27]:25, delay=2.1, delays=0.01/0.13/0.63/1.4, dsn=2.0.0, status=sent (250 2.0.0 OK 1285007676 f9si4898321vbf.12)
Sep 20 14:34:36 server1 postfix/qmgr[1065]: 134DD104307: removed

```

---

