---
title: "Problem postfix -&gt; mysql"
date: 2009-08-12
forum: Server Platforms
---

### Post by unartic on 2009-08-12
Hi there,
 
As I'm totaly new to Linux I'm trying to setup a mailserver on Ubuntu 8.04 server. Therefor I'm following the instructions from Flurdy.
 
After installing and configuring according to the 'manual', I needed to test if postfix worked with mySql.
 
I'm able to connect via telnet to postfix and manyaly sendout an e-mail. (ehlo, mail from, rcpt to, data, quit). The last lines are:
 
----------
quit
221 2.0.0 Bye
Connection closed by foreign host.
You have new mail in /var/mail/administrator
----------
 
Checking out /var/mail/administrator it apears to be empty. According to the mysql user record it should use: home: /var/spool/mail/virtual, maildir: root
 
At first I there was an error in /var/log/mysql.err saing it could not lookup the alias-table. After editing te postfix-mysql files changing the user to root (just for testing purposes), I tried again sending an e-mail. The error log now remaind empty.
 
As the instruction from Flurdy indicated, there should me some log in /var/log/mysql.log. However, this file remains empty.
 
Debugging information states this:
------------
- Check file permission in postfix folder
- Chroot problem, set all services in master.cf to n in chroot column
- Check if mysql socket exists*
- Try changing host in the postfix mysql files between localhost, 127.0.0.1 and real ip. This will result in it trying socket and tcp alternatively.*
- Spelling mistake in postfix mysql files. (Extra spaces?)*
------------
The lines marked with a '*' I've done. But the first and maybe the most obvious one: 'Check file permission in postfix folder' I couldn't find out how to do.
 
So, please advice me what to do next in order to get postfix with mysql working.
 
Kind regards!

---

### Post by localfiend on 2009-08-12
I'm having problems with this same setup, though mine are slightly different.  [http://ubuntuforums.org/showthread.php?t=1237947](http://ubuntuforums.org/showthread.php?t=1237947)

I believe the mysql log by default is located in /var/log/mysql/mysql.log - check there to get the info you're after.  Correct me if I'm wrong, but if you are storing your e-mail virtually then it's all located in a file, rather than a folder.  So its not something you can browse to normally.

---

### Post by unartic on 2009-08-12
Thanx for your reply. The folder you're suggesting is empty.

---

