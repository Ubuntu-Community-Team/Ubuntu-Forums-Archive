---
title: "Postfix adds Trailing Slash to Users?!"
date: 2011-05-11
forum: Server Platforms
---

### Post by precinct25 on 2011-05-11
I followed this tutorial to setup a mail server, followed it to the letter, double/triple/quadruple checked everything for human error, and I can't find anything.

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

What's happening is it seems that postfix is adding a trailing slash to usernames when it does the user lookup, so they don't exist and then fail. I've attached the log below. Please if anyone has any idea as to why this is happening, let me know! I'm starting to lose my mind!

```
May 11 01:06:27 vmail postfix/smtpd[1688]: connect from localhost[127.0.0.1]
May 11 01:06:55 vmail postfix/smtpd[1688]: 3372E982BC: client=localhost[127.0.0.1]
May 11 01:07:18 vmail postfix/cleanup[1691]: 3372E982BC: message-id=<20110511080655.3372E982BC@vmail.domain.com>
May 11 01:07:18 vmail postfix/qmgr[1686]: 3372E982BC: from=<user@domain.com>, size=365, nrcpt=1 (queue active)
May 11 01:07:19 vmail postfix/virtual[1692]: 3372E982BC: to=<bob/@domain.com>, orig_to=<bob@domain.com>, relay=virtual, delay=29, delays=29/0.01/0/0.06, dsn=5.1.1, status=bounced (unknown user: "bob/@domain.com")
May 11 01:07:19 vmail postfix/cleanup[1691]: 09ABB982BE: message-id=<20110511080719.09ABB982BE@vmail.domain.com>
May 11 01:07:19 vmail postfix/qmgr[1686]: 09ABB982BE: from=<>, size=2237, nrcpt=1 (queue active)
May 11 01:07:19 vmail postfix/bounce[1693]: 3372E982BC: sender non-delivery notification: 09ABB982BE
May 11 01:07:19 vmail postfix/qmgr[1686]: 3372E982BC: removed
May 11 01:07:20 vmail postfix/smtp[1695]: 09ABB982BE: to=<user@domain.com>, relay=ASPMX.L.GOOGLE.com[74.125.93.27]:25, delay=1.5, delays=0.01/0/0.14/1.3, dsn=2.0.0, status=sent (250 2.0.0 OK 1305101240 z1si17087865qcq.41)
May 11 01:07:20 vmail postfix/qmgr[1686]: 09ABB982BE: removed
May 11 01:07:21 vmail postfix/smtpd[1688]: disconnect from localhost[127.0.0.1]

```

I'm on Ubuntu 10.04.2 LTS. :confused:

---

### Post by precinct25 on 2011-05-11
Anyone have any idea, this is really driving us nuts! :confused:

---

