---
title: "Posfix Issue -"
date: 2008-11-11
forum: Server Platforms
---

### Post by bruparel on 2008-11-11
I am experiencing sporadic problems with my postfix email server where the email being sent is bounced due to reasons unknown to me.  Here are the snippets from the server log:

Nov  6 10:53:44 app postfix/smtp[29135]: 21B7B1134DB2: to=<jill.jones@gmx.com>, relay=mx0.gmx.com[74.208.5.90], delay=2, status=bounced (host mx0.gmx.com[74.208.5.90] said: 550-5.7.1 {mx-us007} Sorry, your helo has been denied. 550 5.7.1 ( [http://portal.gmx.net/serverrules](http://portal.gmx.net/serverrules) ) (in reply to RCPT TO command))
Nov  6 10:53:44 app postfix/cleanup[29134]: 727E51134DD8: message-id=<20081106105344.727E51134DD8@playful>
Nov  6 10:53:44 app postfix/qmgr[7744]: 727E51134DD8: from=<>, size=51875, nrcpt=1 (queue active)
Nov  6 10:53:44 app postfix/qmgr[7744]: 21B7B1134DB2: removed
Nov  6 10:53:44 app postfix/smtp[29136]: 727E51134DD8: to=<jill.jones@gmx.com>, relay=mx0.gmx.com[74.208.5.90], delay=0, status=bounced (host mx0.gmx.com[74.208.5.90] said: 550-5.7.1 {mx-us007} Sorry, your helo has been denied. 550 5.7.1 ( [http://portal.gmx.net/serverrules](http://portal.gmx.net/serverrules) ) (in reply to RCPT TO command))
Nov  6 10:53:44 app postfix/qmgr[7744]: 727E51134DD8: removed
Nov  6 10:54:20 app postfix/smtpd[29131]: connect from localhost[127.0.0.1]
Nov  6 10:54:20 app postfix/smtpd[29131]: 44D231134DB2: client=localhost[127.0.0.1]
Nov  6 10:54:20 app postfix/cleanup[29134]: 44D231134DB2: message-id=<4912ccdc37d8a_500015555558e70088d@acsol.tmail>
Nov  6 10:54:20 app postfix/smtpd[29131]: disconnect from localhost[127.0.0.1]
Nov  6 10:54:20 app postfix/qmgr[7744]: 44D231134DB2: from=<jill.jones@gmx.com>, size=129926, nrcpt=3 (queue active)
Nov  6 10:54:21 app postfix/smtp[29147]: 44D231134DB2: to=<bccmail@virtualjobcoach.com>, relay=aspmx.l.google.com[72.14.253.27], delay=1, status=sent (250 2.0.0 OK 1225968861 y25si2988431pod.23)
Nov  6 10:54:21 app postfix/smtp[29135]: 44D231134DB2: to=<jill.jones@gmx.com>, relay=mx0.gmx.com[74.208.5.90], delay=1, status=bounced (host mx0.gmx.com[74.208.5.90] said: 550-5.7.1 {mx-us006} Sorry, your helo has been denied. 550 5.7.1 ( [http://portal.gmx.net/serverrules](http://portal.gmx.net/serverrules) ) (in reply to RCPT TO command))
Nov  6 10:54:28 app postfix/smtp[29136]: 44D231134DB2: to=<amy.tinkler@icaruspartnership.com>, relay=mailserver.icaruspartnership.com[217.33.43.80], delay=8, status=bounced (host mailserver.icaruspartnership.com[217.33.43.80] said: 550 5.7.1 Sender ID (PRA) Not Permitted (in reply to end of DATA command))
Nov  6 10:54:28 app postfix/cleanup[29134]: 2BFFE1134DD8: message-id=<20081106105428.2BFFE1134DD8@playful>
Nov  6 10:54:28 app postfix/qmgr[7744]: 2BFFE1134DD8: from=<>, size=52327, nrcpt=1 (queue active)
Nov  6 10:54:28 app postfix/qmgr[7744]: 44D231134DB2: removed

I experienced a similar problem this morning on one of our staging servers with the IP address:  206.251.244.42 (with domain name staging.virtualjobcoach.com) when I tried to send a test email to my own yahoo account.  See the log snippet below:

Nov 11 15:12:27 staging postfix/cleanup[13075]: 975834BC001: message-id=<20081111151227.GA13070@staging.virtualjobcoach.com>
Nov 11 15:12:27 staging postfix/qmgr[22692]: 975834BC001: from=<deploy@staging.virtualjobcoach.com>, size=2397, nrcpt=1 (queue active)
Nov 11 15:12:27 staging postfix/smtp[13076]: connect to g.mx.mail.yahoo.com[209.191.118.103]: server refused to talk to me: 421 Message from (206.251.244.42) temporarily deferred - 4.16.50. Please refer to [http://help.yahoo.com/help/us/mail/defer/defer-06.html](http://help.yahoo.com/help/us/mail/defer/defer-06.html)   (port 25)
Nov 11 15:12:27 staging postfix/smtp[13076]: connect to a.mx.mail.yahoo.com[67.195.168.31]: server refused to talk to me: 421 Message from (206.251.244.42) temporarily deferred - 4.16.50. Please refer to [http://help.yahoo.com/help/us/mail/defer/defer-06.html](http://help.yahoo.com/help/us/mail/defer/defer-06.html)   (port 25)
Nov 11 15:12:28 staging postfix/smtp[13076]: 975834BC001: host e.mx.mail.yahoo.com[216.39.53.1] said: 421 Message temporarily deferred - 4.16.51. Please refer to [http://help.yahoo.com/help/us/mail/defer/defer-06.html](http://help.yahoo.com/help/us/mail/defer/defer-06.html) (in reply to end of DATA command)
Nov 11 15:12:28 staging postfix/smtp[13076]: 975834BC001: to=<john.jones@yahoo.com>, relay=d.mx.mail.yahoo.com[66.196.82.7], delay=1, status=sent (250 ok dirdel)
Nov 11 15:12:28 staging postfix/qmgr[22692]: 975834BC001: removed

Thing is: most of the emails get through fine.  Any guidance in troubleshooting this would be greatly appreciated.  The servers are running Ubuntu 6.06 LTS.

Thanks.

Bharat

---

### Post by MJN on 2008-11-11
All the clues are there, have you followed the URLs for further instruction?

> **bruparel said:**
> Nov  6 10:53:44 app postfix/smtp[29135]: 21B7B1134DB2: to=<jill.jones@gmx.com>, relay=mx0.gmx.com[74.208.5.90], delay=2, status=bounced (host mx0.gmx.com[74.208.5.90] said: 550-5.7.1 {mx-us007} Sorry, your helo has been denied. 550 5.7.1 ( [http://portal.gmx.net/serverrules](http://portal.gmx.net/serverrules) ) (in reply to RCPT TO command))This one is complaining at your 'HELO' declaration. What is your server name as dictated by Postfix? (post /etc/postfix/main.cf if you don't know - specifically $myhostname and/or $smtp_helo_name)

> Nov 11 15:12:27 staging postfix/smtp[13076]: connect to a.mx.mail.yahoo.com[67.195.168.31]: server refused to talk to me: 421 Message from (206.251.244.42) temporarily deferred - 4.16.50. Please refer to [http://help.yahoo.com/help/us/mail/defer/defer-06.html](http://help.yahoo.com/help/us/mail/defer/defer-06.html)   (port 25)Yahoo thinks you're a spammer. Are you? Are any of your users? Have you followed their guidance? Do your e-mails eventually get delivered?

Mathew

---

### Post by bruparel on 2008-11-12
Thank you Matt.  I set myhostname variable in the main.cf file and that resolved the issue.  I appreciate your help.
Regards,
Bharat

---

