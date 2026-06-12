---
title: "No mails in INBOX"
date: 2010-02-02
forum: Server Platforms
---

### Post by LMSSML on 2010-02-02
Hi there,

I've got the following

postfix
saslauth
apache2
roundcube
squirrelmail
ispconfig
webmin
courier
dovecot -> last thing to install but without resolution.
php
mysql

Hi there

I've got installed mail server and configured squirrelmail instead of smtp with sendmail.

I can send emails but in my INBOX i couldn't find any emails, althouth I have used the following

postqueue -p 

AE0A883A78      672 Fri Jan 29 23:56:47  user@domain
                                         user@domain

8074B825B2    77285 Tue Feb  2 12:02:05  logcheck
                                         logcheck

5D96581366    40135 Thu Jan 28 05:02:06  logcheck
                                         logcheck

52CAB81363    38310 Thu Jan 28 03:02:05  logcheck
                                         logcheck

8FFE1801A3      674 Wed Jan 27 15:45:18  user1@domain
                                         user@domain

2DDD58257F    13394 Fri Jan 29 03:02:06  logcheck
                                         logcheck

9083A81367    39663 Thu Jan 28 06:02:05  logcheck
                                         logcheck

A78DA825AF      668 Tue Feb  2 11:21:28  user@domain
                                         user@domain

44D2D8135B   155759 Fri Jan 29 12:00:39  logcheck
                                         logcheck

87CF183A8C    13394 Sat Jan 30 17:02:05  logcheck
                                         logcheck

C54FC83A79    81082 Sat Jan 30 00:02:05  logcheck
                                         logcheck

04595825AE      667 Tue Feb  2 11:14:23  user@domain
                                         user@domain

5BA54825B4      668 Tue Feb  2 12:12:11  user@domain
                                         user@domain

9048D83AAD    21378 Mon Feb  1 01:02:05  logcheck
                                         logcheck

1BE6581368     4656 Thu Jan 28 06:53:27  root
                                         root



and i can see the emails but could not recive emails on squirrelmail on INBOX.

I don't have problems for sending,moving or deleting  e-mails.

but i do have problems the emails could come to my INBOX

---

### Post by LMSSML on 2010-02-02
HI there

Anyone who could help ?

Thanks in advanced

---

### Post by ThomasEriksen on 2010-02-02
It seems there is a bug in the latest ubuntu maildrop update.

I used this solution:

[http://www.howtoforge.com/forums/showpost.php?p=218260&postcount=9](http://www.howtoforge.com/forums/showpost.php?p=218260&postcount=9)

---

### Post by LMSSML on 2010-02-02
Hi ThomasEriksen,

Thanks for your help.

It could be might help me but it dosen't.

If you have any try I would like to try.


Thanks in advanced.

---

### Post by mgichoga on 2010-02-03
Could you post the permissions on your /var/mail?
I ran into this problem once where an update messed up the permissions on this folder and dovecot could not read it.

--

M gichoga

---

### Post by LMSSML on 2010-02-03
Hi mgichoga,

My permissions on /var/mail are these.

drwxrwsr-x  3 root mail  4.0K 2010-01-19 11:37 mail

---

### Post by mgichoga on 2010-02-03
Permissions look okay. Are you still using dovecot? If so where is your inbox locations pointing to?

in /etc/dovecot/dovecot.conf there is an directive pointing to the inboxes .eg

> mail_location = mbox:~/mail:INBOX=/var/mail/%u

Make sure you read through the directions.

Other suggestions:
As you log in to your webmail consult your log file to see what errors you are getting. 

> tail -f /var/log/syslog

This will give you live output and you might catch some more error messages.

---

### Post by LMSSML on 2010-02-03
Hi there,

I've removed courier and installed dovecot after applying the path of mailbox and see the syslog I've got this

Syslog

> mail dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Feb  3 17:13:50 mail dovecot: auth-worker(default): mysql: Connect failed to localhost (dbispconfig): Access denied for user 'ispconfig'@'localhost' (using password: YES) - waiting for 1 seconds before retry                               

And another thing now I can't login to the machine.

Log from tail -f /var/log/mail.log

 > mail dovecot: imap-login: Aborted login (auth failed, 1 attempts): method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured 


Try to make  test on webmin with fetchmail and have the following:


 > Authorization failure on [email]user@doomain.pt@localhost.locald[/email]omain
fetchmail: IMAP> A0006 LOGOUT
fetchmail: IMAP< A0005 BAD Error in IMAP command received by server.
fetchmail: IMAP< * BYE Logging out
fetchmail: IMAP< A0006 OK Logout completed.
fetchmail: 6.3.9-rc2 querying localhost (protocol IMAP) at Wed 03 Feb 2010 05:20:33 PM WET: poll completed
fetchmail: Query status=3 (AUTHFAIL)
fetchmail: normal termination, status 3

---

### Post by mgichoga on 2010-02-03
I know almost nothing about ISPconfig but it might be that you have the wrong username/password for dovecot to connect to the mysql database. If it was working before with dovecot probably after re-installing it you need to enter the authentications details. On the /etc/dovecot directory there is a dovecote-sql.conf, although I doubt if that's where its looking for the dbispconfig database.

> And another thing now I can't login to the machine.

Did you change the squirrelmail config to make sure you are using the dovecot imap server?

---

### Post by LMSSML on 2010-02-04
No ideas with dovecot

> auth-worker(default): mysql: Connect failed to localhost (dbispconfig): Access denied for user 'ispconfig'@'localhost' (using password: YES) - waiting for 75 seconds before retry
Feb 4 19:14:09 mail dovecot: auth-worker(default): sql(<user>,<ip>): Password query failed: Not connected to database.

Any ideas because probably it could be this point of my failure to access  (login), thing that I could do using courier.

Probably the query of dovecot-sql.conf is correct.

> connect = host=localhost dbname=dbispconfig user=ispconfig password=password


If I change the variable %u to user through mysql I found one result.

> password_query = SELECT password FROM mail_user WHERE email = '%u'

If I change the variable %u to user through mysql I found one result.

> user_query = SELECT email FROM mail_user WHERE email = '%u'

But every time i try to login through squirrelmail I get username and password I've got the following:

> Unknown user or password incorrect.

Any help people.

---

### Post by mgichoga on 2010-02-04
To verify you have the correct password, try logging into mysql through command line

> mysql -u ispconfig -p

It will ask you for a password. If it does not let you in then the password set is not correct.

---

### Post by Rich78 on 2010-02-04
I don't know whether your issue is related to mine, but does your MTA (in your case Postfix) have any mail in the mailbox first?

I only ask as I'm using Exim4 as my MTA and I can send mail via command line but cannot receive mail from external, even though I've pointed the MX records to the server.

---

### Post by LMSSML on 2010-02-04
Hi there,

Thanks for the awnsers,but at the moment I've tried

> mysql -D dbispconfig -u ispconfig -p
Enter password:
ERROR 1045 (28000): Access denied for user 'ispconfig'@'localhost' (using password: YES)

> mysql -u ispconfig -p
ERROR 1045 (28000): Access denied for user 'ispconfig'@'localhost' (using password: YES)


Rich78 when using courier I can sent emails but couldn't recive in squirrelmail INBOX with squirrelmail configuration to sendmail instead of smtp but 
my INBOX it's always empty althouh i could see mails in queue from postfix if I do 

> postqueue -p 

but I think it could probably having to do it with my maildir or mbox path.


I even think that my dovecot version could be with some bug versionof dovecot 1.1.11



Last note

I could change the password for ispconfig user through webmin and the I run 

> mysql -D dbispconfig -u ispconfig -p
Enter password:
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 915
Server version: 5.1.37-1ubuntu5 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>

---

### Post by mgichoga on 2010-02-04
Have you tried reflecting the password you changed to the config? I believe this should let you at least login.

---

### Post by LMSSML on 2010-02-05
I'm facing another problem:

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'ispconfig'@'localhost' (using password: YES) in /usr/local/ispconfig/interface/lib/classes/db_mysql.inc.php on line 73

tried to  enter in webpage of ispconfig.

---

### Post by LMSSML on 2010-02-05
I've made uninstaller and the installed again ispconfig 

so at the moment it's ok.

but still have the same problem.

> Feb 5 13:39:18 mail dovecot: auth-worker(default): mysql: Connect failed to localhost (dbispconfig): Access denied for user 'ispconfig'@'localhost' (using password: YES) - waiting for 75 seconds before retry
Feb 5 13:39:18 mail dovecot: auth-worker(default): sql(<user>,<ip>): Password query failed: Not connected to database
Feb 5 13:39:20 mail dovecot: imap-login: Aborted login (auth failed, 1 attempts): user=, method=PLAIN, rip=<ip>, lip=<ip>, secured

---

### Post by LMSSML on 2010-02-05
I people,

Have removed dovecot and installed courier same problem that I posted in the beginig of topic.

No mails INBOX.

---

### Post by LMSSML on 2010-02-08
Any help ?


Could not recive emails on INBOX.

Using postfix +courier+sasl+squirrelmail.

I've tried to use outlook express froma pc to configure account and make it download emails.

In my hosts files I have to put the following.

Since I have an email server with same name .

<ip> <hostname>

if I use ping <hostname> it resolves to <ip>.

I read it somewhere to use bind9 is it that the cause of not reciving emails on squirrelmail INBOX ?

Any help ?

Thanks.

---

### Post by LMSSML on 2010-02-09
Hi people tried with outlook express and get the following errors reciving and sending mail

For sending:

Your server has unexpectedly terminated the connection. Possible causes for this include server problems, network problems, or a long period of inactivity. Account: '<mail.example.com>', Server: '<mail.example.com>', Protocol: SMTP, Port: 25, Secure(SSL): No, Error Number: 0x800CCC0F

For reciving:

The connection to the server has failed. Account: '<mail.example.com>', Server: '<mail.example.com>', Protocol: POP3, Port: 110, Secure(SSL): No, Socket Error: 10060, Error Number: 0x800CCC0E

Any help ?

---

