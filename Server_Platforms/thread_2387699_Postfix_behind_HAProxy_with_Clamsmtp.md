---
title: "Postfix behind HAProxy with Clamsmtp"
date: 2018-03-22
forum: Server Platforms
---

### Post by tslogick on 2018-03-22
I am trying to setup a 2 node postfix cluster for SMTP relay behind an HAProxy.  Everything works fine on each node using round robin from the HAProxy until I load ClamAV to do virus scanning of the SMTP traffic.  I followed this document to setup ClamAV, [https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto), but am getting this message in the mail.log

relay=127.0.0.1[127.0.0.1]:10026, delay=1016, delays=1011/0.01/5/0, dsn=4.4.2, status=deferred (lost connection with 127.0.0.1[127.0.0.1] while receiving the initial server greeting)

Mar 22 11:14:13 lppostfix300 clamsmtpd: 100004: accepted connection from: 127.0.0.1
Mar 22 11:14:18 lppostfix300 postfix/smtpd[40151]: warning: haproxy read: timeout error
Mar 22 11:14:18 lppostfix300 postfix/smtpd[40151]: connect from unknown[unknown]
Mar 22 11:14:18 lppostfix300 postfix/smtpd[40151]: disconnect from unknown[unknown] commands=0/0


Is there a setting in the HAProxy or Postfix that I am missing to get ClamAV to work?

---

