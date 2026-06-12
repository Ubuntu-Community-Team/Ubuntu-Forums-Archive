---
title: "telnet imap"
date: 2008-08-13
forum: Server Platforms
---

### Post by gishaust on 2008-08-13
I have been trying to setup squirrel mail and could not get it to work.

I found out the squirrel mail relys on imap so I ssh into the server and then sudo su --> telnet localhost 143 --> and below is what I got next
I have postfix with a mysql database as a backend.

```

Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2005 Double Precision, Inc.  See COPYING for distribution information.
Connection closed by foreign host.

```

courier is working,

```

 netstat -tap | grep imap
tcp6       0      0 [::]:imaps              [::]:*                  LISTEN      5849/couriertcpd
tcp6       0      0 [::]:imap2              [::]:*                  LISTEN      5801/couriertcpd

```


My question is what do I do next to fix the problem and what log do I look in there is no courier log?


gishaust

---

### Post by MJN on 2008-08-13
Hi gishaust,
 
Presumably Squirrelmail us giving you some sort for error? If so, what is it?
 
(Incidentally, you don't need to be su to telnet to the IMAP server.)
 
Mathew

---

### Post by gishaust on 2008-08-13
thanks for the reply mjn 

The error I get is the following
```

ERROR: Connection dropped by IMAP server.

```

However I also have postfix.admin and if I try and sent an email to that it gets into the database but it won't tell me in postfix.admin and it needs the imap software to work as well.


I belief it works something like this. 
Mysql <-------imap(as the middleman)------> Squirrelmail Postfix admin (which need imap to talk to the mysql server)

so that is why I believe it to be an imap issue. What do you think!!

---

### Post by MJN on 2008-08-13
Are you sure there's no log entries from Courier? Even in /var/log/mail.log?

I'm not familiar with the operation of Courier (I use Dovecot myself) but there surely must be something being logged somewhere.

Mathew

---

### Post by gishaust on 2008-08-13
this is the mail log

```

Aug 14 07:03:16 ubuntumta1 authdaemond: modules="authmysql", daemons=5
Aug 14 07:03:16 ubuntumta1 authdaemond: Installing libauthmysql
Aug 14 07:03:16 ubuntumta1 authdaemond: Installation complete: authmysql
Aug 14 07:03:17 ubuntumta1 postfix/master[4109]: daemon started -- version 2.5.1, configuration /etc/postfix
Aug 14 07:07:52 ubuntumta1 imapd: Connection, ip=[::ffff:127.0.0.1]
Aug 14 07:07:52 ubuntumta1 imapd: chdir Maildir: No such file or directory
Aug 14 12:57:57 ubuntumta1 authdaemond: modules="authmysql", daemons=5
Aug 14 12:57:57 ubuntumta1 authdaemond: Installing libauthmysql
Aug 14 12:57:57 ubuntumta1 authdaemond: Installation complete: authmysql
Aug 14 12:57:58 ubuntumta1 postfix/master[4297]: daemon started -- version 2.5.1, configuration /etc/postfix

```

---

### Post by gishaust on 2008-08-13
please disregard the last post I tried that send the mail yesterday on the 13th and this is what is says.

```

Aug 13 15:44:00 ubuntumta1 imapd: Connection, ip=[::ffff:127.0.0.1]
Aug 13 15:44:00 ubuntumta1 imapd: sales@www.dbs.com: chdir(home/vmail) failed!!
Aug 13 15:44:00 ubuntumta1 imapd: error: No such file or directory
Aug 13 15:44:00 ubuntumta1 imapd: LOGIN FAILED, user=sales@www.dbs.com, ip=[::ffff:127.0.0.1]
Aug 13 15:44:00 ubuntumta1 imapd: authentication error: No such file or directory
Aug 13 15:45:34 ubuntumta1 postfix/smtpd[5172]: dict_eval: const  mail
Aug 13 15:45:34 ubuntumta1 postfix/smtpd[5172]: dict_eval: const  ipv4
Aug 13 15:45:34 ubuntumta1 postfix/smtpd[5172]: name_mask: ipv4
Aug 13 15:45:34 ubuntumta1 postfix/smtpd[5172]: dict_eval: const  ubuntumta1.purencool.com
Aug 13 15:45:34 ubuntumta1 postfix/smtpd[5172]: dict_eval: const  dbs.com

```

I know that the user exist if I cd home/vmail/sales@www.dbs.com it is in the dir. and the email is in the dir as well.I did not know that the mail.log was the log file. Does anyone have any ideas?

---

### Post by MJN on 2008-08-14
The key errors are the first and second lines - Courier is trying to change to /home/vmail but that directory doesn't exist.

A Google search suggests this is a fairly common occurance and can be fixed by either sending a mail to your sales users, whereby Courier will automatically create the necessary folders, or doing it manually using the maildirmake command.

I'd like to provide more specific guidance but as I said I don't use Courier so I'd be learning it from scratch

Mathew

---

### Post by gishaust on 2008-08-15
I have had enough is dovecot easy to configure?

---

### Post by MJN on 2008-08-15
Insofar that it will likely work for you out of the box, yes.
 
Mathew

---

