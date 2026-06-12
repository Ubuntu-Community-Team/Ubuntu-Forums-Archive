---
title: "Postfix MySQL issues"
date: 2010-12-17
forum: Server Platforms
---

### Post by jbtito03 on 2010-12-17
Hi...

I am setting up postfix+dovecot+mysql+postfixadmin.... so far so good. 

But i cannot retrieve mail from my adress as i get this errors in my logfile:

Dec 17 19:59:41 melionet postfix/postfix-script[18071]: refreshing the Postfix mail system
Dec 17 19:59:42 melionet postfix/master[17625]: reload configuration /etc/postfix
Dec 17 20:00:04 melionet postfix/trivial-rewrite[26189]: warning: connect to mysql server localhost: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Dec 17 20:00:04 melionet postfix/trivial-rewrite[26189]: fatal: mysql:/etc/postfix/mysql/relay-domains.cf(0,lock|fold_fix): table lookup problem
Dec 17 20:00:04 melionet postfix/cleanup[11762]: 880DB37B2CF4: message-id=<20101217185934.880DB37B2CF4@mail.melionet.com>
Dec 17 20:00:05 melionet postfix/qmgr[1925]: warning: problem talking to service rewrite: Success
Dec 17 20:00:05 melionet postfix/master[17625]: warning: process /usr/lib/postfix/trivial-rewrite pid 26189 exit status 1
Dec 17 20:00:05 melionet postfix/master[17625]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Dec 17 20:00:06 melionet postfix/trivial-rewrite[26191]: warning: connect to mysql server localhost: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Dec 17 20:00:06 melionet postfix/trivial-rewrite[26191]: fatal: mysql:/etc/postfix/mysql/relay-domains.cf(0,lock|fold_fix): table lookup problem
Dec 17 20:00:07 melionet postfix/qmgr[1925]: warning: problem talking to service rewrite: Success
Dec 17 20:00:07 melionet postfix/master[17625]: warning: process /usr/lib/postfix/trivial-rewrite pid 26191 exit status 1


Well... the mysqld.sock file is alive and kickin, mysql works localy under unix socket ok for other applications. 

Has anyone a idea what the problem might be, cause after days of googling and following multiple tutorials i am getting a bit crazy about this one. 

Cheers...

JB

---

### Post by jbtito03 on 2010-12-18
**bump**

---

### Post by jbtito03 on 2010-12-19
Hi

Solved the issue - changed "localhost" in my virtual domains conf files for postfix to 127.0.0.1 as it is in my conf file for mysql and now it works. 

How stupid... :S

Cheers..

JB

---

