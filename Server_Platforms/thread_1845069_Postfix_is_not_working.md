---
title: "Postfix is not working"
date: 2011-09-16
forum: Server Platforms
---

### Post by rafiqasad on 2011-09-16
Hello Everyone,

I am facing a strange problem with one of my Ubuntu servers. I had sendmail as mailing agent on my machine, but now i stop sendmail and install postfix as a mail sending agent. Now when i am trying to send email either through command or by php script, it said email send but in actual email is not delivering. when i check the mailq, all emails are in mailq. then i check the error log file.


root@www:/# tail -f /var/log/mail.err
Sep 16 13:47:45 www postfix/smtp[17599]: fatal: open database /etc/postfix/tls_per_site.db: No such file or directory
Sep 16 13:51:04 www postfix/smtp[7265]: fatal: open database /etc/postfix/tls_per_site.db: No such file or directory
Sep 16 13:52:05 www postfix/smtp[1827]: fatal: open database /etc/postfix/tls_per_site.db: No such file or directory
Sep 16 13:52:07 www postfix/smtp[3080]: fatal: open database /etc/postfix/tls_per_site.db: No such file or directory
Sep 16 13:53:08 www postfix/smtp[7880]: fatal: open database /etc/postfix/tls_per_site.db: No such file or directory
Sep 16 13:54:09 www postfix/smtp[13332]: fatal: open database /etc/postfix/tls_per_site.db: No such file or directory
Sep 16 14:03:00 www postfix/smtp[3233]: fatal: open database /etc/postfix/tls_per_site.db: No such file or directory
Sep 16 14:04:01 www postfix/smtp[9570]: fatal: open database /etc/postfix/tls_per_site.db: No such file or directory
Sep 16 14:05:02 www postfix/smtp[22135]: fatal: open database /etc/postfix/tls_per_site.db: No such file or directory
Sep 16 14:06:03 www postfix/smtp[15676]: fatal: open database /etc/postfix/tls_per_site.db: No such file or directory
Sep 16 14:07:04 www postfix/smtp[30547]: fatal: open database /etc/postfix/tls_per_site.db: No such file or directory
Sep 16 14:08:05 www postfix/smtp[3736]: fatal: open database /etc/postfix/tls_per_site.db: No such file or directory
Sep 16 14:09:06 www postfix/smtp[11876]: fatal: open database /etc/postfix/tls_per_site.db: No such file or directory
Sep 16 14:10:07 www postfix/smtp[19892]: fatal: open database /etc/postfix/tls_per_site.db: No such file or directory


Can someone please guide me what the problem is and how I can solve this problem.

Thanks and best wishes.
Best regards.

---

### Post by gombadi on 2011-09-16
> 
fatal: open database /etc/postfix/tls_per_site.db: No such file or directory


It seems to be looking for a file and can not find it. How did you install postfix? Did you follow a guide - if so which one?

How have you configured postfix? Can you provide us with some details?

---

