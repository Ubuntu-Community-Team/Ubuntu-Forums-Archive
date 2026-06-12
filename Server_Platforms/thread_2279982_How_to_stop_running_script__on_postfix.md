---
title: "How to stop running script  on postfix ?"
date: 2015-05-27
forum: Server Platforms
---

### Post by rhandy2 on 2015-05-27
I have some script running every 30 minutes send emails from [EMAIL="example@example.com"]example@example.com[/EMAIL], to [EMAIL="example@example.com"]example@example.com[/EMAIL].  

example is real email, I not put here only for example.

But I can´t find what it is.

I try grep -ri "example@example.com" .

But I can´t find anything ???


.```
/log/mail.log:May 27 05:07:26 myhostname postfix/qmgr[1644]: 1C8C810144D: from=<example@example.com>, size=422, nrcpt=1 (queue active)
./log/mail.log:May 27 05:07:26 myhostname postfix/qmgr[1644]: 420BF1014BE: from=<example@example.com>, size=2312, nrcpt=1 (queue active)
./log/mail.log:May 27 05:07:56 myhostname postfix/smtp[28856]: 1C8C810144D: to=<example@example.com>, relay=none, delay=109441, delays=109411/0.01/30/0, dsn=4.4.1, status=deferred (connect to example.com[2606:2800:220:1:248:1893:25c8:1946]:25: Network is unreachable)
./log/mail.log:May 27 05:07:56 myhostname postfix/smtp[28857]: 420BF1014BE: to=<example@example.com>, relay=none, delay=109440, delays=109410/0.01/30/0, dsn=4.4.1, status=deferred (connect to example.com[93.184.216.34]:25: Connection timed out)
./log/mail.log:May 27 05:37:26 myhostname postfix/qmgr[1644]: 625F2101468: from=<example@example.com>, size=409, nrcpt=1 (queue active)
./log/mail.log:May 27 05:37:56 myhostname postfix/smtp[29860]: 625F2101468: to=<example@example.com>, relay=none, delay=109510, delays=109480/0.01/30/0, dsn=4.4.1, status=deferred (connect to example.com[93.184.216.34]:25: Connection timed out)
./log/mail.log:May 27 06:17:26 myhostname postfix/qmgr[1644]: 1C8C810144D: from=<example@example.com>, size=422, nrcpt=1 (queue active)
./log/mail.log:May 27 06:17:26 myhostname postfix/qmgr[1644]: 420BF1014BE: from=<example@example.com>, size=2312, nrcpt=1 (queue active)
./log/mail.log:May 27 06:17:56 myhostname postfix/smtp[31163]: 420BF1014BE: to=<example@example.com>, relay=none, delay=113640, delays=113610/0.01/30/0, dsn=4.4.1, status=deferred (connect to example.com[2606:2800:220:1:248:1893:25c8:1946]:25: Network is unreachable)
./log/mail.log:May 27 06:17:56 myhostname postfix/smtp[31162]: 1C8C810144D: to=<example@example.com>, relay=none, delay=113641, delays=113611/0.01/30/0, dsn=4.4.1, status=deferred (connect to example.com[2606:2800:220:1:248:1893:25c8:1946]:25: Network is unreachable)
./log/mail.log:May 27 06:47:26 myhostname postfix/qmgr[1644]: 625F2101468: from=<example@example.com>, size=409, nrcpt=1 (queue active)
./log/mail.log:May 27 06:47:56 myhostname postfix/smtp[32477]: 625F2101468: to=<example@example.com>, relay=none, delay=113710, delays=113680/0.01/30/0, dsn=4.4.1, status=deferred (connect to example.com[93.184.216.34]:25: Connection timed out)
./log/mail.log:May 27 07:27:26 myhostname postfix/qmgr[1644]: 1C8C810144D: from=<example@example.com>, size=422, nrcpt=1 (queue active)
./log/mail.log:May 27 07:27:26 myhostname postfix/qmgr[1644]: 420BF1014BE: from=<example@example.com>, size=2312, nrcpt=1 (queue active)
./log/mail.log:May 27 07:27:56 myhostname postfix/smtp[1287]: 420BF1014BE: to=<example@example.com>, relay=none, delay=117840, delays=117810/0.01/30/0, dsn=4.4.1, status=deferred (connect to example.com[2606:2800:220:1:248:1893:25c8:1946]:25: Network is unreachable)
./log/mail.log:May 27 07:27:56 myhostname postfix/smtp[1286]: 1C8C810144D: to=<example@example.com>, relay=none, delay=117841, delays=117811/0.01/30/0, dsn=4.4.1, status=deferred (connect to example.com[93.184.216.34]:25: Connection timed out)
./log/mail.log:May 27 07:57:26 myhostname postfix/qmgr[1644]: 625F2101468: from=<example@example.com>, size=409, nrcpt=1 (queue active)
./log/mail.log:May 27 07:57:56 myhostname postfix/smtp[2367]: 625F2101468: to=<example@example.com>, relay=none, delay=117910, delays=117880/0.01/30/0, dsn=4.4.1, status=deferred (connect to example.com[93.184.216.34]:25: Connection timed out)
./log/mail.log:May 27 08:37:26 myhostname postfix/qmgr[1644]: 1C8C810144D: from=<example@example.com>, size=422, nrcpt=1 (queue active)
./log/mail.log:May 27 08:37:26 myhostname postfix/qmgr[1644]: 420BF1014BE: from=<example@example.com>, size=2312, nrcpt=1 (queue active)
./log/mail.log:May 27 08:37:56 myhostname postfix/smtp[3635]: 420BF1014BE: to=<example@example.com>, relay=none, delay=122040, delays=122010/0.01/30/0, dsn=4.4.1, status=deferred (connect to example.com[93.184.216.34]:25: Connection timed out)
./log/mail.log:May 27 08:37:56 myhostname postfix/smtp[3634]: 1C8C810144D: to=<example@example.com>, relay=none, delay=122041, delays=122011/0.01/30/0, dsn=4.4.1, status=deferred (connect to example.com[2606:2800:220:1:248:1893:25c8:1946]:25: Network is unreachable)
./log/mail.log:May 27 09:07:26 myhostname postfix/qmgr[1644]: 625F2101468: from=<example@example.com>, size=409, nrcpt=1 (queue active)
./log/mail.log:May 27 09:07:56 myhostname postfix/smtp[4650]: 625F2101468: to=<example@example.com>, relay=none

```

---

### Post by SeijiSensei on 2015-05-27
That's not a script.  You have a message stuck in the queue addressed to @example.com, the official domain name set aside for demonstrations.  (See [http://www.example.com/](http://www.example.com/).)  Like all mail servers it periodically tries to resend the message and naturally fails. Use the procedures described here to flush the queue: [http://www.tech-g.com/2012/07/15/inspecting-postfixs-email-queue/](http://www.tech-g.com/2012/07/15/inspecting-postfixs-email-queue/)

---

### Post by rhandy2 on 2015-05-27
Oh !!! I ´m so blind!!!!

Thank you!!!! you solve my problem!

---

### Post by SeijiSensei on 2015-05-27
We're all blind at times.  Glad I could help.

---

