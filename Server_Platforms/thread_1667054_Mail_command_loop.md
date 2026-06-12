---
title: "Mail command loop"
date: 2011-01-14
forum: Server Platforms
---

### Post by ipersubario on 2011-01-14
Hi all,

My operating system: Ubuntu 10.04.1 LTS server

I've installad and configured postfix, procmail, fetchmail and dovecot-imap. All work perfectly!

here is my question: when I send mail with mail command I receive the CC: and Subject: question, next I put the data and I finish with a dot in a blank line. Program mail goes in loop. I must press Ctrl-Z to kill it

instead when I digit:
echo "mail text" | mail root@mydomain -s "subject"

mail arrived!


I don't understand why program mail goes in loop... Log files are empty: syslog, mail.log dmesg


Anyone?

Thanks for help

---

