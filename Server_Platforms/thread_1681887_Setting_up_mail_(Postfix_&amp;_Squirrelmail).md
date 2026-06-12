---
title: "Setting up mail (Postfix &amp; Squirrelmail)"
date: 2011-02-04
forum: Server Platforms
---

### Post by jrtboht on 2011-02-04
I had mail set up fine using ispconfig3 (but couldn't get my websites to work) so I uninstalled ispconfig3 and used [this]("http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04") tutorial to set up mail manually (the only exception is I use mysql workbench instead of phpmyadmin).  However, I haven't been able to get mail working.  When I try to log into squirrelmail I get

**ERROR: Connection dropped by IMAP server.**

I've gone through the tutorial twice and sent a "first email" to the account that is set up.  Here's is my mail log when I start the server and I try to log in to squirrelmail.

[PHP]Feb  4 23:00:02 webserver postfix/pickup[1551]: 57EC2880272: uid=33 from=<www-data>
Feb  4 23:00:02 webserver postfix/cleanup[1710]: 57EC2880272: message-id=<20110205040002.57EC2880272@webserver.myhome.westell.com>
Feb  4 23:00:02 webserver postfix/qmgr[1552]: 57EC2880272: from=<www-data@webserver.myhome.westell.com>, size=916, nrcpt=1 (queue active)
Feb  4 23:00:02 webserver amavis[1253]: (01253-01) (!)connect_to_sql: unable to connect to DSN 'DBI:mysql:database=dbispconfig;host=127.0.0.1;port=3306': U$
Feb  4 23:00:02 webserver amavis[1253]: (01253-01) (!!)TROUBLE in process_request: connect_to_sql: unable to connect to any dataset at (eval 115) line 241,$
Feb  4 23:00:02 webserver amavis[1253]: (01253-01) (!)Requesting process rundown after fatal error
Feb  4 23:00:02 webserver postfix/smtp[1713]: 57EC2880272: to=<www-data@webserver.myhome.westell.com>, orig_to=<www-data>, relay=127.0.0.1[127.0.0.1]:10024$
Feb  4 23:02:29 webserver imapd: Connection, ip=[::1]
Feb  4 23:02:29 webserver imapd: chdir annarrankings.com/jeremy/: No such file or directory
Feb  4 23:02:29 webserver imapd: jeremy@annarrankings.com: No such file or directory[/PHP]Obviously the directories aren't be automatically set up (I added a directory for vmail manually).  I also notice that something is trying to access dbispconfig database but for the life of me can't figure what remnant code for ispconfig is still around.  Any help would be greatly appreciated, Thanks

Side note: I'm using ubuntu server 10.10 (upgraded from 10.04) and have no database named dbispconfig

---

### Post by HermanAB on 2011-02-05
Hmm, the first time, it can easily take 2 weeks to get a postfix/apache/dovecot mail system to work.  While it is a good way to learn how mail works, you should consider installing Citadel instead, if you are mainly interested in having a working system without wasting any time.  

Citadel is hands down the easiest Linux mail system and installs in about 20 minutes and then it 'Just Works' (TM).  The Easy Install script creates a simple, yet fully featured mail system which can handle thousands of users and terabytes of mail.  

Have a look at [http://citadel.org](http://citadel.org) it my save you a lot of hair.

---

### Post by jrtboht on 2011-02-05
Does Citadel support virtual domains and virtual users?  My webserver currently holds 5 domains and each domain will need a handful of emails.

---

### Post by HermanAB on 2011-02-05
Yes, Citadel does everything, including multiple domains, but the user names must be unique.  If you have multiple domains with the same user names on multiple domains, belonging to different people, then you need multiple Citadel servers.

---

