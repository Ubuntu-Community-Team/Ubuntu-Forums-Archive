---
title: "Mail.log errors"
date: 2006-06-02
forum: Server Platforms
---

### Post by rensu on 2006-06-02
Could someone help me to find out what problems do I have :S
Those are the errors what my log report:

Jun  3 00:50:35 localhost postfix/smtpd[21554]: warning: problem talking to service rewrite: Success
Jun  3 00:50:35 localhost postfix/master[8579]: warning: process /usr/lib/postfix/trivial-rewrite pid 25427 exit status 1
Jun  3 00:50:35 localhost postfix/master[8579]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Jun  3 00:50:56 localhost postfix/smtpd[21554]: fatal: watchdog timeout
Jun  3 00:50:57 localhost postfix/master[8579]: warning: process /usr/lib/postfix/smtpd pid 21554 exit status 1
Jun  3 00:50:57 localhost postfix/master[8579]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jun  3 00:51:35 localhost postfix/trivial-rewrite[25432]: warning: connect to mysql server 127.0.0.1: Client does not support authentication protocol requested by server; consider upgrading MySQL client
Jun  3 00:51:35 localhost postfix/trivial-rewrite[25432]: fatal: mysql:/etc/postfix/mysql_alias.cf(0,100): table lookup problem
Jun  3 00:51:36 localhost postfix/master[8579]: warning: process /usr/lib/postfix/trivial-rewrite pid 25432 exit status 1
Jun  3 00:51:36 localhost postfix/master[8579]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling

---

### Post by Alvadore on 2006-07-07
Seems like we both have the same problem with postfix/trivial-rewrite.  Have you found a sollution yet?

---

### Post by smeago on 2008-05-05
Bro. I have same problem with my postfix. Have you been able to resolve it? Please let me know how you did resolves it.

---

### Post by diagonallemma on 2008-05-29
Might be a different problem. But after the latest apt-get upgrade on my 6.06 server last week, I got lots of

postfix/trivial-rewrite[3625]: fatal: mysql:/etc/postfix/mysql_alias.cf(0,100): table lookup problem

errors because the mail user couldn't log in to mysql anymore. I had to go into mysql as admin and grant the privileges again.

---

