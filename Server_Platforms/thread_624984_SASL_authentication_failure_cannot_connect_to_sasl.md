---
title: "SASL authentication failure: cannot connect to saslauthd server: No such file or dire"
date: 2007-11-27
forum: Server Platforms
---

### Post by zcox on 2007-11-27
Hi - I have an Ubuntu 7.04 server with a mail server I installed by following this guide:

[http://howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy](http://howtoforge.com/virtual_postfix_mysql_quota_courier_ubuntu_edgy)

Everything was working great, multiple email accounts on multiple domains working fine.  Now I set up Trac on the same machine and am trying to send out notification emails using SMTP.

However, each time Trac tries to send an email, I get the following in /var/log/mail.info (domain & IP changed to protect the innocent):

Nov 27 19:14:44 54700 postfix/smtpd[17849]: connect from xxx.com[xxx.xxx.xxx.xxx]
Nov 27 19:14:44 54700 postfix/smtpd[17849]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
Nov 27 19:14:44 54700 postfix/smtpd[17849]: warning: SASL authentication failure: Password verification failed
Nov 27 19:14:44 54700 postfix/smtpd[17849]: warning: xxx.com[xxx.xxx.xxx.xxx]: SASL PLAIN authentication failed: generic failure
Nov 27 19:14:44 54700 postfix/smtpd[17849]: lost connection after AUTH from xxx.com[xxx.xxx.xxx.xxx]
Nov 27 19:14:44 54700 postfix/smtpd[17849]: disconnect from xxx.com[xxx.xxx.xxx.xxx]

I'm most concerned with the "warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory" line.

Does anyone know why I might be getting that warning?

---

