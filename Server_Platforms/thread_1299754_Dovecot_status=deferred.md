---
title: "Dovecot status=deferred"
date: 2009-10-24
forum: Server Platforms
---

### Post by PWS on 2009-10-24
Hi

I am trying to set up a mail server with postfix and dovecot. However I am getting a status = deferred error instead of status = sent in my log and the mail will not be sent. Sending a mail to hotmail/gmail works fine though.

I used this tutorial [http://workaround.org/articles/ispmail-etch/](http://workaround.org/articles/ispmail-etch/)

And later updated to the Lenny tutorial [http://workaround.org/ispmail/lenny](http://workaround.org/ispmail/lenny)

The mailserver is running on Ubuntu 9.04 (desktop).

Log
```
Oct 24 14:29:19 pws-desktop postfix/qmgr[17007]: C01F71FE146: from=<steve@example.com>, size=341, nrcpt=1 (queue active)
Oct 24 14:29:19 pws-desktop postfix/pipe[17035]: C01F71FE146: to=<john@example.com>, relay=dovecot, delay=0.22, delays=0.15/0.01/0/0.06, dsn=4.3.0, status=deferred (temporary failure)

```Thanks

---

