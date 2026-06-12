---
title: "Unable to send mail on hotmail in Zimbra E-mail server."
date: 2014-06-16
forum: Server Platforms
---

### Post by Tarun_Gupta on 2014-06-16
Unable to send mail on Hotmail server.

```

Jun 16 11:41:14 msdplantations postfix/amavisd/smtpd[21803]: connect from localhost[127.0.0.1]
Jun 16 11:41:14 msdplantations postfix/amavisd/smtpd[21803]: E6806280D72: client=localhost[127.0.0.1]
Jun 16 11:41:14 msdplantations postfix/cleanup[21795]: E6806280D72: message-id=<719873953.26.1402899070175.JavaMail.zimbra@domainname.com>
Jun 16 11:41:14 msdplantations postfix/amavisd/smtpd[21803]: disconnect from localhost[127.0.0.1]
Jun 16 11:41:14 msdplantations postfix/qmgr[16822]: E6806280D72: from=<admin@domainname.com>, size=1600, nrcpt=1 (queue active)
Jun 16 11:41:14 msdplantations amavis[16426]: (16426-04) FWD from <admin@domainname.com> -> <mukeshkumar76@hotmail.com>,BODY=7BIT 250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as E6806280D72
Jun 16 11:41:14 msdplantations amavis[16426]: (16426-04) Passed CLEAN {RelayedOutbound}, ORIGINATING_POST/MYNETS LOCAL [127.0.0.1]:35825 [103.16.140.33] <admin@domainname.com> -> <mukeshkumar76@hotmail.com>, Queue-ID: CC054280D77, Message-ID: <719873953.26.1402899070175.JavaMail.zimbra@domainname.com>, mail_id: 1JzM8Cx5w3ht, Hits: -3.451, size: 1200, queued_as: E6806280D72, 4075 ms
Jun 16 11:41:14 msdplantations postfix/smtp[21801]: CC054280D77: to=<mukeshkumar76@hotmail.com>, relay=127.0.0.1[127.0.0.1]:10032, delay=4.1, delays=0.05/0.01/0.01/4.1, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as E6806280D72)
Jun 16 11:41:14 msdplantations postfix/qmgr[16822]: CC054280D77: removed
**Jun 16 11:41:17 msdplantations postfix/smtp[21804]: E6806280D72: to=<mukeshkumar76@hotmail.com>, relay=mx3.hotmail.com[65.55.92.168]:25, delay=2.7, delays=0.02/0.01/1.1/1.6, dsn=2.0.0, status=sent (250  <719873953.26.1402899070175.JavaMail.zimbra@domainname.com> Queued mail for delivery)**

```

---

### Post by Habitual on 2014-06-18
**status=sent **says to me...it will get there.

---

