---
title: "Postfix bounced back any emails received from the internet"
date: 2016-12-27
forum: Server Platforms
---

### Post by fallex on 2016-12-27
/var/log/mail.log
Dec 27 16:05:18 mail postfix/smtpd[18695]: disconnect from mail.example.ca[127.0.0.1]
Dec 27 16:05:18 mail postfix/local[18700]: 74FF5220670: to=<freddie@example.ca>, relay=local, delay=0.01, delays=0.01/0/0/0, dsn=2.0.0, status=sent (delivered to mailbox)
Dec 27 16:05:18 mail postfix/qmgr[18690]: 74FF5220670: removed
Dec 27 16:05:18 mail amavis[17075]: (17075-16) Passed CLEAN {RelayedInbound}, [74.125.82.52]:35825 <example@gmail.com> -> <freddie@example.ca>, Queue-ID: B7DEA22066C, Message-ID: <CAARXFsYs7cuTzvuFLS6uxnkrzfdCBO4O4SHgEOAEMb3_ZFNZVA@mail.gmail.com>, mail_id: DSnzfz0QF6Vd, Hits: -0.1, size: 2003, queued_as: 74FF5220670, dkim_sd=20161025:gmail.com, 1388 ms
Dec 27 16:05:18 mail postfix/smtp[18691]: B7DEA22066C: to=<freddie@example.ca>, relay=127.0.0.1[127.0.0.1]:10024, delay=1.7, delays=0.35/0/0/1.4, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as 74FF5220670)
Dec 27 16:05:18 mail postfix/qmgr[18690]: B7DEA22066C: removed
Dec 27 16:06:09 mail dovecot: imap-login: Login: user=<freddie@example.ca>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=18731, secured, session=<5zVFvKxEnAB/AAAB>
Dec 27 16:06:09 mail dovecot: imap(freddie@example.ca): Disconnected: Logged out in=90 out=891
Dec 27 16:07:09 mail dovecot: imap-login: Login: user=<freddie@example.ca>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=18734, secured, session=<uerYv6xEoAB/AAAB>
Dec 27 16:07:09 mail dovecot: imap(freddie@example.ca): Disconnected: Logged out in=90 out=891

Bounced message:
[FONT=arial]Final-Recipient: rfc822; [/FONT][EMAIL="support@fallex.ca"]support@exmaple.ca[/EMAIL]
[FONT=arial]Original-Recipient: [/FONT][EMAIL="rfc822%3Bsupport@fallex.ca"]rfc822;support@example.ca[/EMAIL]
[FONT=arial]Action: failed[/FONT]
[FONT=arial]Status: 5.1.1[/FONT]
[FONT=arial]Diagnostic-Code: X-Postfix; unknown user: "support"
[/FONT]
Does anyone see any reason why postfix keeps bouncing back any emails from the internet? I can forward emails to the internet and send and receive emails locally.

Please advise..thanks

---

