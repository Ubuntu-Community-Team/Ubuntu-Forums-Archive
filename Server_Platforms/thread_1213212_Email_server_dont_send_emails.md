---
title: "Email server dont send emails"
date: 2009-07-14
forum: Server Platforms
---

### Post by Dr.Thr@x on 2009-07-14
Hi. I have problem. I cant send emails on my E-Mail server (Postfix+Courier+MySQL...)
I read this [tutorial]("http://flurdy.com/docs/postfix/") and configure to Postfix + Courier IMAP + MySQLwithou firewall (Not Advanced mail server in tut.). I create user in MySQL and login to the mailbox. I can receive email but i cant send email. I have all ports open, DNS Configured... I tried send mail via telnet but it didnt work. I always receive mailer daemon:

Undelivered Mail Returned to Sender from  [EMAIL="MAILER-DAEMON@wzk.cz"]MAILER-DAEMON@wzk.cz[/EMAIL] (Mail Delivery System):

> This is the mail system at host Server.localdomain.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<thrax@email.cz>: mail for smtp.wzk.cz loops back to myself 
 Reporting-MTA: dns; Server.localdomain
X-Postfix-Queue-ID: 90EA9110320
X-Postfix-Sender: rfc822; [EMAIL="test@wzk.cz"]test@wzk.cz[/EMAIL]
Arrival-Date: Tue, 14 Jul 2009 13:21:33 +0200 (CEST)

Final-Recipient: rfc822; [EMAIL="thrax@email.cz"]thrax@email.cz[/EMAIL]
Action: failed
Status: 5.4.6
Diagnostic-Code: X-Postfix; mail for smtp.wzk.cz loops back to myself
And there is log:

```
Jul  8 20:26:26 Server imapd: LOGIN, user=test@wzk.cz, ip=[::ffff:192.168.1.1], port=[44325], protocol=IMAP
Jul  8 20:26:26 Server imapd: LOGOUT, user=test@wzk.cz, ip=[::ffff:192.168.1.1], headers=0, body=0, rcvd=10, sent=83, time=0
Jul  8 20:26:34 Server postfix/smtpd[13234]: connect from my.router[192.168.1.1]
Jul  8 20:26:34 Server postfix/smtp[13261]: warning: host mail.wzk.cz[85.132.218.29]:25 greeted me with my own hostname Server.localdomain
Jul  8 20:26:34 Server postfix/smtp[13261]: warning: host mail.wzk.cz[85.132.218.29]:25 replied to HELO/EHLO with my own hostname Server.localdomain
Jul  8 20:26:34 Server postfix/smtp[13261]: D1CFE1102E7: to=<thrax@email.cz>, relay=mail.wzk.cz[85.132.218.29]:25, delay=20, delays=0.03/0.01/20/0, dsn=5.4.6, status=bounced (mail for smtp.wzk.cz loops back to myself)
Jul  8 20:26:34 Server postfix/smtpd[13234]: disconnect from my.router[192.168.1.1]
Jul  8 20:26:34 Server postfix/cleanup[13238]: E57761102E8: message-id=<20090708182634.E57761102E8@Server.localdomain>
Jul  8 20:26:34 Server postfix/bounce[13264]: D1CFE1102E7: sender non-delivery notification: E57761102E8
Jul  8 20:26:34 Server postfix/qmgr[13233]: E57761102E8: from=<>, size=2263, nrcpt=1 (queue active)
Jul  8 20:26:34 Server postfix/qmgr[13233]: D1CFE1102E7: removed
Jul  8 20:26:34 Server postfix/virtual[13239]: E57761102E8: to=<test@wzk.cz>, relay=virtual, delay=0.02, delays=0.01/0/0/0, dsn=2.0.0, status=sent (delivered to maildir)
Jul  8 20:26:34 Server postfix/qmgr[13233]: E57761102E8: removed
Jul  8 20:26:55 Server imapd: Connection, ip=[::ffff:192.168.1.1]
Jul  8 20:26:55 Server authdaemond: received auth request, service=imap, authtype=login
```And when i try to log-in to mail via Thunderbird, show me error:

> Not connect to smtp.wzk.cz, connection was rejectedIf you understand help me. THX. 
(Sorry my english is bad...)

---

