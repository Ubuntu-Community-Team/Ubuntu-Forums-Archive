---
title: "Upgraded distro, can't connect email accounts with Thunderbird but can with LiveMail"
date: 2014-08-15
forum: Server Platforms
---

### Post by surfdude on 2014-08-15
Greetins,

I just upgraded my server to 14.04 as I was having troubles with fail2ban and figured I would update everything while I was at it.  After getting everything else working I noticed that my email stopped working on Thunderbird but it was working totally fine with Live Mail.  They both have identical settings.  I can send and receive perfectly using Live Mail but Thunderbird does nothing when checking mail and I get an error that it cannot connect to SMTP and to check my settings.  SMTP is using TLS on 587 and IMAP is using TLS on 993.

In my mail.log I get:

```
warning: hostname XX-XX-XX-XX.res.bhn.net does not resolve to address XX.XX.XX.XX: Name or service not known
Aug 15 17:32:36 ServerName postfix/smtpd[5219]: connect from unknown[XX.XX.XX.XX]
Aug 15 17:32:36 ServerName postfix/smtpd[5219]: lost connection after STARTTLS from unknown[XX.XX.XX.XX]
```

That is all I can see that is out of ordinary and mail.err is empty.  I am not really sure where to go with this as a different email client on the same machine works flawlessly.  Thanks for any insight and direction you can point me in.

---

### Post by surfdude on 2014-08-16
For what it's worth,  I have traced this to an issue with Avast! ssl scanning.  Although I Am still unable to get it to work.

---

