---
title: "Setting up mail on 12.10"
date: 2013-05-06
forum: Server Platforms
---

### Post by bullet333 on 2013-05-06
I'm trying to setup sendmail on my Ubuntu VM to automatically email my windows exchange account but it's not working properly.

My Ubuntu is setup as a proxy server for web filtering.  It is not a part of the domain and it not authenticated nor do I plan it to be anytime soon.  I do not want to set this server as a mail host as this is only used for alerts and log files.  Only one user (me/admin) will be using this server.

I figured out that Webmin has a Sendmail and Read User Mail modules. I've been messing around with that and was able to send mail to my exchange server manually, but for some reason logrotate cannot send mail automatically. It produces the following errors:

> [COLOR=#333333]/etc/cron.daily/logrotate:[/COLOR]
mail: cannot send message: Process exited with a non-zero statuserror: mail command failed for /var/tmp/syslog.1run-parts: /etc/cron.daily/logrotate exited with return code 1/etc/cron.daily/sarg: [COLOR=#333333]SARG: Period covered by log files: 02/05/2013-02/05/2013[/COLOR]

> [COLOR=#333333]The original message was received at Fri, 3 May 2013 07:46:27 -0400[/COLOR]
from root@localhost ----- The following addresses had permanent fatal errors -----<[FONT=Verdana]myemail@domain.com[/FONT]> (reason: 550 5.1.1 <myemail@domain.com>... User unknown) (expanded from: <[FONT=Verdana]myemail@domain.com[/FONT][FONT=Verdana]>)[/FONT]
----- Transcript of session follows -----... while talking to [127.0.0.1]:>>> DATA<<< 550 5.1.1 <[FONT=Verdana]myemail@domain.com[/FONT][FONT=Verdana]>... User unknown[/FONT]
550 5.1.1 <[FONT=Verdana]myemail@domain.com[/FONT][FONT=Verdana]>... User unknown [/FONT][COLOR=#333333]<<< 503 5.0.0 Need RCPT (recipient)[/COLOR]

It appears that it's trying to resolve my exchange account via 127.0.0.1 (localhost) which is wrong.  I'm not exactly sure how to change the "Remote Mail Server" address.  These Sendmail configurations are rather confusing.  Another service I recently installed and configured, Monit has no issues in sending mail automatically.

---

### Post by matt_symes on 2013-05-06
Thread moved to **Server Platforms.**

---

### Post by SeijiSensei on 2013-05-06
In sendmail, you can designate a "relay host," which in this case would be the Exchange server.  If you put the Exchange server's hostname after the DS line in sendmail.cf, all mail will be forwarded to that machine for further processing and delivery.

```
DSexchange.example.com
```

If, for some reason you do not have a working DNS so that the server's name cannot be resolved, you can replace the name with an IP address in square brackets like this:

```
DS[10.10.10.10]
```

or you could add an entry to /etc/hosts with the IP address and name of the Exchange server and use its name as in the first example.

---

### Post by bullet333 on 2013-05-06
I believe I resolved this issue by switching to Postfix instead of Sendmail.  I was reading another thread stating that Sendmail is rather complicated and hard to configure for noobs (like me).  I installed Postfix, modified a few things, restarted the server and got some emails!

Thanks!

---

