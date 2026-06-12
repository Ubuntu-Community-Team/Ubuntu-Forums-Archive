---
title: "Configuring sendmail"
date: 2011-09-28
forum: Server Platforms
---

### Post by skeath on 2011-09-28
At my work, we have set up an internal Linux server running Ubuntu to do some data processing.  While it has access to the Internet, and can do one-way communication with our web server (co-located offsite), it is not itself a web server.  It has a small website on it, a frontend for the data processing, but that can only be accessed from inside our building.  It is inside a firewall, and does not have a public IP.

I have verified that cron works, and will run scripts, but cron email does not.  It purports to be sending a report to root, but there is no root mailbox, and even if there were, that does me no good.  We would want reports to come to our company emails on our public domain.

I tried using the error_log() function in PHP, but that also fails, although I have verified that PHP is pointing to the right location for sendmail.

Access to both of these methods would be best, but we need at least for cron email to work, to get error reports.

Evidently, there is something missing in the setup.  If anyone can suggest a path forward, I would be grateful.

Thanks,

Sandy Keathley

---

### Post by SeijiSensei on 2011-09-28
Add this line to the top of the crontab:

```
MAILTO=someone@example.com
```

with the address to which you want cron errors sent.

Try testing your sendmail installation by using

```

$ telnet localhost 25
[sendmail header appears]
ehlo localhost
[sendmail replies]
mail from: root@localhost
[replies]
rcpt to: someone@example.com
[replies]
data
this is a test
.
quit
[replies]

```

Replace "someone@example.com" with a legitimate address.

---

### Post by skeath on 2011-09-28
Thank you very much!  Sendmail reported that it worked, but I did not get the email, so I tried it again with my personal address, and that worked, so the problem is with our Exchange server (of course).  I can get around that by sending to another of our domains that is not so encumbered, and forward from there.

Thanks,

SK

---

