---
title: "SMTP server with postfix. Getting email impossible"
date: 2015-03-27
forum: Server Platforms
---

### Post by max.bonvin on 2015-03-27
Hi,

I can send an email to localy or to another ip. BUT I can't get email !

my maillog: (Note: EMAILFROMGMAIL, EMAILFROMMYSERVER, MYWEBSITE, are not the true value of course)
```
Mar 27 17:10:48 MYWEBSITE postfix/smtpd[28835]: connect from mail-oi0-f45.google.com[209.85.218.45]
Mar 27 17:10:49 MYWEBSITE postfix/smtpd[28835]: 5B11DA159F: client=mail-oi0-f45.google.com[209.85.218.45]
Mar 27 17:10:49 MYWEBSITE postfix/cleanup[28842]: 5B11DA159F: message-id=<CAP3QWtS8HsV+xVesNZ2eca2oUDcu342yHePWzsZd2=uLyFVJ3w@mail.gmail.com>
Mar 27 17:10:49 MYWEBSITE postfix/qmgr[28291]: 5B11DA159F: from=<EMAILFROMGMAIL>, size=1713, nrcpt=1 (queue active)
Mar 27 17:10:49 MYWEBSITE postfix/smtpd[28835]: disconnect from mail-oi0-f45.google.com[209.85.218.45]
Mar 27 17:10:54 MYWEBSITE postfix/smtpd[28850]: connect from unknown[127.0.0.1]
Mar 27 17:10:54 MYWEBSITE postfix/smtpd[28850]: E06A2A15D8: client=unknown[127.0.0.1]
Mar 27 17:10:54 MYWEBSITE postfix/cleanup[28842]: E06A2A15D8: message-id=<CAP3QWtS8HsV+xVesNZ2eca2oUDcu342yHePWzsZd2=uLyFVJ3w@mail.gmail.com>
Mar 27 17:10:54 MYWEBSITE postfix/qmgr[28291]: E06A2A15D8: from=<EMAILFROMGMAIL>, size=2551, nrcpt=1 (queue active)
Mar 27 17:10:54 MYWEBSITE postfix/smtpd[28850]: disconnect from unknown[127.0.0.1]
Mar 27 17:10:54 MYWEBSITE amavis[28221]: (28221-03) Passed CLEAN {RelayedInbound}, [209.85.218.45]:36668 [209.85.218.45] <EMAILFROMGMAIL> -> <EMAILFROMMYSERVER>, Message-ID: <CAP3QWtS8HsV+xVesNZ2eca2oUDcu342yHePWzsZd2=uLyFVJ3w@mail.gmail.com>, mail_id: GFjzLIP0NOpo, Hits: 2.339, size: 1713, queued_as: E06A2A15D8, dkim_sd=20120113:gmail.com, 5278 ms
Mar 27 17:10:54 MYWEBSITE postfix/smtp[28843]: 5B11DA159F: to=<EMAILFROMMYSERVER>, relay=127.0.0.1[127.0.0.1]:10024, delay=5.6, delays=0.31/0/0/5.3, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as E06A2A15D8)
Mar 27 17:10:54 MYWEBSITE postfix/qmgr[28291]: 5B11DA159F: removed

```

I can't understand this log.... This log appears when I send an email from my Gmail account to my server.

Someone know how can I get an mail with Postfix on Cent-OS ? Someone know how to fix this ? Is it an error ?

I'm realy sorry if I'm in the bad section (or in the bad forum xD)

If you want other code of file, just ask me.

Best regards,

flechenoir.

---

### Post by TheFu on 2015-03-28
Perhaps if you step back and describe the setup?  Please start with DNS settings, since those are key for receiving email.

---

### Post by SeijiSensei on 2015-03-28
Have you read this?  [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

---

