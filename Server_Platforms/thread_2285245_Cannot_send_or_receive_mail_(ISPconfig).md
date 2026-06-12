---
title: "Cannot send or receive mail (ISPconfig)"
date: 2015-07-04
forum: Server Platforms
---

### Post by ali6 on 2015-07-04
Hello,
So last night I updated ISPconfig and ever since then I have been unable to receive and send emails. I have checked the logs and so far every time I try and send an email I get this message in the logs located at /var/log/mail.log[spoiler]```

Jul  4 10:41:49 server1 postfix/smtpd[10377]: connect from unknown[xxxx]
Jul  4 10:41:49 server1 postfix/smtpd[10377]: Anonymous TLS connection established from unknown[xxxx]: TLSv1.2 with cipher ECDHE-RSA-AES256-SHA384 (256/256 bits)
Jul  4 10:41:51 server1 postfix/smtpd[10377]: 875FC50C1625: client=unknown[xxxx], sasl_method=PLAIN, sasl_username=ali@.com
Jul  4 10:41:52 server1 postfix/cleanup[10387]: 875FC50C1625: message-id=<etPan.55979c4d.3d77fc16.67b@Alis-MacBook-Pro.local>
Jul  4 10:41:52 server1 postfix/qmgr[9021]: 875FC50C1625: from=<ali@.com>, size=1620, nrcpt=1 (queue active)
Jul  4 10:41:52 server1 postfix/qmgr[9021]: warning: connect to transport private/amavis: No such file or directory
Jul  4 10:41:52 server1 postfix/error[10388]: 875FC50C1625: to=<theofficial@gmail.com>, relay=none, delay=0.84, delays=0.81/0/0/0.03, dsn=4.3.0, status=deferred (mail transport unavailable)
Jul  4 10:41:52 server1 postfix/smtpd[10377]: disconnect from unknown[xxxx]
Jul  4 10:41:53 server1 dovecot: imap-login: Login: user=<ali@.com>, method=PLAIN, rip=xxxxx, lip=xxxx, mpid=10394, TLS, session=<R9P6pAgauAAl0yAd>
Jul  4 10:41:56 server1 dovecot: imap-login: Login: user=<ali@.com>, method=PLAIN, rip=xxxx, lip=xxxxx, mpid=10396, TLS, session=<1xcupQgaugAl0yAd>
Jul  4 10:42:04 server1 dovecot: imap(ali@a.com): Connection closed in=1526 out=6020
Jul  4 10:42:06 server1 dovecot: imap(ali@.com): Connection closed in=66 out=821
Jul  4 10:42:27 server1 dovecot: imap-login: Login: user=<ali@.com>, method=PLAIN, rip= xxxx, lip= xxxx, mpid=10408, TLS, session=<Y8gBpwgaXwAl0yAd>
Jul  4 10:42:28 server1 dovecot: imap-login: Login: user=<ali@.com>, method=PLAIN, rip= xxxx, lip= xxxx, mpid=10410, TLS, session=<VMgVpwga1AAl0yAd>
```
[/spoiler]




Thanks in advance for the help
-Ali

---

### Post by ali6 on 2015-07-07
Bump

---

### Post by PaulW2U on 2015-07-07
*Thread moved to **Server Platforms**.*

---

