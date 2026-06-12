---
title: "mail loops back to myself"
date: 2010-08-03
forum: Server Platforms
---

### Post by VRage on 2010-08-03
Hey guys,
Followed the tutorial [here]("http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04-p4") to setup postfix with virtual users and courier and must have messed up somewhere as I can send emails as well as receive from within the server but when I send them from outsite I get the following in mail.log:

> 
visual-rebirth postfix/cleanup[23708]: 152F737680B0: message-id=<20100728140051.152F737680B0@visual-rebirth.com>
visual-rebirth postfix/bounce[24473]: 0FA1A37680AE: sender non-delivery notification: 152F737680B0
visual-rebirth postfix/qmgr[3693]: 152F737680B0: from=<>, size=2839, nrcpt=1 (queue active)
visual-rebirth postfix/trivial-rewrite[23710]: warning: do not list domain visual-rebirth.com in BOTH mydestination and virtual_mailbox_domains
visual-rebirth postfix/qmgr[3693]: 0FA1A37680AE: removed Jul 28 visual-rebirth postfix/smtp[24472]: 152F737680B0: to=<xxxxxxxx@visual-rebirth.com>, relay=none, delay=0.01, delays=0/0/0/0, dsn=5.4.6, status=bounced (mail for mail.visual-rebirth.com loops
back to myself)
visual-rebirth postfix/qmgr[3693]: 152F737680B0: removed


Any ideas on where I might have messed up?

Thanks in advance!

---

### Post by wesg on 2010-09-07
I'm having the same problem, and have been fighting with postfix for a while. No one knows a potential solution?

---

