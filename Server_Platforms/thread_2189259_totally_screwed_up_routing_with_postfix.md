---
title: "totally screwed up routing with postfix"
date: 2013-11-21
forum: Server Platforms
---

### Post by clearski on 2013-11-21
I've got a Postfix server on the LAN, which is used by a few users for exchanging emails inside our private domain.

Each user has a LAN e-mail account (e.g. user@our-private-domain), which can be accessed using MUAs connecting to local servers on 465 and 993, and a public Gmail account. Every user connects directly to Google's mailservers, using the same MUAs and the same ports, but they just use remote servers to send and retrieve mail.

I'd like to use our *local *smtp server to receive and forward every single email, regardless of the domain, so that no MUA will connect directly to smtp.gmail.com. Mails directed to LAN users would be delivered to local inboxes, and mails directed to domains outside our private perimeter would be delivered by Postfix to Gmail's public servers, using each user's own credentials.

I've done some (bad :)) things here and now even the local mail doesn't get delivered to mailboxes... I am not sure I even followed the right tutorial, or maybe it's just a bad config issue.

Any reference to follow or help would be appreciated!

Thank you.

---

### Post by clearski on 2013-11-21
I made some progress. Now all local mail is routed correctly.

Postfix is trying to relay to gmail, but I still get an error.

```
Nov 21 23:46:11 host postfix/smtp[5275]: 0494882C44: to=<username@gmail.com>, relay=smtp.gmail.com, relay=smtp.gmail.com[173.194.69.108]:587, delay=0.46, delays=0.01/0.02/0.4/0.04, dsn=5.5.1, status=bounced (host smtp.gmail.com[173.194.69.108] said: 530-5.5.1 Authentication Required. Learn more at 530 5.5.1 http://support.google.com/mail/bin/answer.py?answer=14257 - gsmtp (in reply to MAIL FROM command))
```

The link provided did not help, nor did a bunch of tutorials from the net.

---

### Post by clearski on 2013-11-21
Solved, thanks to this tutorial:

[http://mhawthorne.net/posts/postfix-configuring-gmail-as-relay.html](http://mhawthorne.net/posts/postfix-configuring-gmail-as-relay.html)

One difference is that my sasl_passwd* files are owned by root instead of postfix, as he suggested.

```
Nov 22 00:29:11 host postfix/smtp[3320]: 8546E82C45: to=<user@gmail.com>, relay=smtp.gmail.com[173.194.69.109]:587, delay=1.2, delays=0.02/0.03/0.54/0.6, dsn=2.0.0, delays=0.02/0.03/0.54/0.6, dsn=2.0.0, status=sent (250 2.0.0 OK 1385072951 z6sm29484184bkn.8 - gsmtp)
```

I guess it's time to rest. :)

---

