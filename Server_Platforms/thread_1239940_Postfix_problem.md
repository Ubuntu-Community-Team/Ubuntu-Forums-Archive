---
title: "Postfix problem"
date: 2009-08-14
forum: Server Platforms
---

### Post by unartic on 2009-08-14
Hi!
 
After following Flurdy's howto to setup a mailserver, I manages to get postfix with courier running.
 
The next step I attempted was installing mypfxadmin in order to have a webinterface to configure the whole.
 
However, mypfxadmin uses a differend database structure then the howto from flurdy uses.
 
So I created a different db with the databaselayout from mypfxadmin and edited the .cf-files in /etc/postfix to make sure they connect to the right database. I thought this would be all, but when manualy (telnet) send an email to postfix I get stuck after the ehlo-command. 
 
mail.info says this:
------------------------------------------------------------
Aug 14 04:10:13 ubuntu2 postfix/trivial-rewrite[4873]: fatal: mysql:/etc/postfix/transport.cf(0,lock|fold_fix): table lookup problem
Aug 14 04:10:14 ubuntu2 postfix/smtpd[4868]: warning: problem talking to service rewrite: Success
Aug 14 04:10:14 ubuntu2 postfix/master[4717]: warning: process /usr/lib/postfix/trivial-rewrite pid 4873 exit status 1
Aug 14 04:10:14 ubuntu2 postfix/master[4717]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Aug 14 04:11:14 ubuntu2 postfix/trivial-rewrite[4892]: warning: connect to mysql server localhost: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.soc$
Aug 14 04:11:14 ubuntu2 postfix/trivial-rewrite[4892]: warning: connect to mysql server localhost: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.soc$
Aug 14 04:11:14 ubuntu2 postfix/trivial-rewrite[4892]: fatal: mysql:/etc/postfix/transport.cf(0,lock|fold_fix): table lookup problem
Aug 14 04:11:15 ubuntu2 postfix/smtpd[4868]: warning: problem talking to service rewrite: Success
Aug 14 04:11:15 ubuntu2 postfix/master[4717]: warning: process /usr/lib/postfix/trivial-rewrite pid 4892 exit status 1
Aug 14 04:11:15 ubuntu2 postfix/master[4717]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
------------------------------------------------------------
 
I don't understand the lines about postfix/trivial-rewrite. 
 
From my understanding the data in postfix/transport.cf is wrong so it can't connect to mysql, though, I checked it  a thousend times and even put in the root-user and password to make sure no access problems occur.
 
Please advice me what to do, to solve this problem.
 
Kind regards!

---

### Post by unartic on 2009-08-14
I was able to solve this problem by changing the hosts section from localhost into 127.0.0.1.
 
Why this solved the problem is unclear to me. Can anyone explain?

---

### Post by noway2 on 2009-08-14
Its anecdotal, but I recall reading somewhere that debian based systems sometimes have problems with "localhost" and instead require 127.0.0.1. No explaination was given as to why, but ever since I have just used the IP address.

---

