---
title: "postfix error"
date: 2009-05-07
forum: Server Platforms
---

### Post by _sluimers_ on 2009-05-07
I get this error message in the syslog:

```
May  7 09:26:12 *mydomainname* postfix/qmgr[3140]: 3A06B5648F: removed
May  7 09:26:12 *mydomainname* postfix/smtpd[23923]: disconnect from 82-xx-xx-94.ip.telfort.nl[82.xx.xx.94]
May  7 09:26:13 *mydomainname* postfix/qmgr[3140]: 099465648E: from=<>, size=3597, nrcpt=1 (queue active)
May  7 09:26:13 *mydomainname* postfix/bounce[23922]: 11BAC562A5: sender non-delivery notification: 099465648E
May  7 09:26:13 *mydomainname* postfix/qmgr[3140]: 11BAC562A5: removed
May  7 09:26:13 *mydomainname* postfix/smtpd[23815]: connect from 82-xx-xx-94.ip.telfort.nl[82.xx.xx.94]
May  7 09:26:13 *mydomainname* postfix/smtp[23917]: warning: host mail.*mydomainname*.com[82.xx.xx.94]:25 greeted me with my own hostname *mydomainname*.com
May  7 09:26:13 *mydomainname* postfix/smtp[23917]: warning: host mail.*mydomainname*.com[82.xx.xx.94]:25 replied to HELO/EHLO with my own hostname *mydomainname*.com
May  7 09:26:20 *mydomainname* postfix/smtp[23917]: 099465648E: to=<root@mail.*mydomainname*.com>, relay=mail.*mydomainname*.com[82.xx.xx.94]:25, delay=1.1, delays=1/0/0.15/0, dsn=5.4.6, status=bounced (mail for mail.*mydomainname*.com loops back to myself)
May  7 09:26:20 *mydomainname* postfix/qmgr[3140]: 099465648E: removed
```

What to do?
I don't want mails to be sent to [email]root@mail.mydomainname.com[/email] by the way, but [email]root@mydomainname.com[/email].

---

### Post by _sluimers_ on 2009-05-07
solved by changing /etc/mailname to *mydomainname.com*

---

