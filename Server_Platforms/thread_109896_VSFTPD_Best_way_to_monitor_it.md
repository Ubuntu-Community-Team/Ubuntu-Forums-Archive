---
title: "VSFTPD Best way to monitor it?"
date: 2005-12-29
forum: Server Platforms
---

### Post by jimbodot on 2005-12-29
What is the best way to monitor VSFTPD in real time, some app I could run and would give me full view of the server activities, real time, without running commands

---

### Post by cstudent on 2005-12-29
I use a program called log2mail to monitor the vsftpd.log file for keywords. When it finds a match it emails me the info. log2mail is in the repositories.

---

### Post by fresco on 2006-01-01
Also you can try to issue the following commands:

tail -f /var/log/vsftpd.log (or wherever your vsftpd's log file is located)

or this:

ps -fe | grep vsftpd

---

