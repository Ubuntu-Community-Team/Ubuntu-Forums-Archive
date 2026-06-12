---
title: "logcheck doesn't send mails where I want them"
date: 2006-07-23
forum: Server Platforms
---

### Post by supermihi on 2006-07-23
Hi,
I have serious problems with logcheck on various ubuntu machines. What I want is that the emails from logcheck are sent to my email address.
I use SSMTP as mail forwarder to the "real" smtp from my university. In ssmtp.conf I have the line
```
root="myaddress@mydomain.com"
```

In /etc/cron.d/logcheck, there is an entry "MAILTO=root", so normally all logcheck related mail should go to my account. But if I look into /var/log/mail.log, for every hour, exactly the time cron runs the logcheck command, there appers a line:
```
Jul 23 11:02:37 hostname sSMTP[5940]: Sent mail for logcheck@hostname.department.university.com (221 smtp.department.university.com says goodbye to aserver.department.university.com at Sun Jul 23 11:02:39.) uid=112 username=logcheck outbytes=756
```

So obviously some mails get sent to logcheck@<the machine's hostname>, not to root=my own email address. Where is the problem? It used to work until a few months ago, maybe some upgrade of ssmtp broke my configuration, since this appears on various machines (ubuntu dapper, breezy and debian).

If I tell logcheck.conf not to send mail to "root" but to my own address I get the actual logcheck mail, but still cron sends a mail to the smtp server of the university - and the operator of that server is getting angry because of all that mail. ;)
This really drives me crazy, I already tried lots of settings without success. :(

---

