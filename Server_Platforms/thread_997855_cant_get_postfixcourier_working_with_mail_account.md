---
title: "cant get postfix/courier working with mail account"
date: 2008-11-30
forum: Server Platforms
---

### Post by martien on 2008-11-30
Hello i just installed postfix+courier+squirrelmail+mysql support for virtual users/domains. So i configured squirrelmail to use the imap server and i populate the database with one domain and account for it (the domain is pointed to my server and has mx record). Then i tried to login with the data chosen and squirrelmail comes with error: "Unknown user or password incorrect.". So i opened /var/log/mail.log and here is it:
> Nov 30 15:29:52 stf postfix/trivial-rewrite[8584]: warning: mysql query failed: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FROM domains WHERE domain='gmail.com'' at line 1
Nov 30 15:29:52 stf postfix/trivial-rewrite[8584]: fatal: mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
Nov 30 15:29:53 stf postfix/smtpd[7515]: warning: problem talking to service rewrite: Success
Nov 30 15:29:53 stf postfix/master[7373]: warning: process /usr/lib/postfix/trivial-rewrite pid 8584 exit status 1
Nov 30 15:29:53 stf postfix/master[7373]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling
Nov 30 15:30:32 stf imapd: Connection, ip=[::ffff:127.0.0.1]
Nov 30 15:30:32 stf imapd: LOGIN FAILED, user=webmaster@<mydomainname.tld>, ip=[::ffff:127.0.0.1]
Nov 30 15:30:37 stf imapd: LOGOUT, ip=[::ffff:127.0.0.1], rcvd=56, sent=332
Nov 30 15:30:53 stf postfix/trivial-rewrite[8586]: warning: mysql query failed: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FROM domains WHERE domain='gmail.com'' at line 1
Nov 30 15:30:53 stf postfix/trivial-rewrite[8586]: fatal: mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
Nov 30 15:30:54 stf postfix/smtpd[7515]: warning: problem talking to service rewrite: Success
Nov 30 15:30:54 stf postfix/master[7373]: warning: process /usr/lib/postfix/trivial-rewrite pid 8586 exit status 1
Nov 30 15:30:54 stf postfix/master[7373]: warning: /usr/lib/postfix/trivial-rewrite: bad command startup -- throttling

Here we see the line with wrong sql syntax. The problem is that i've never entered anywhere something about gmail.com (yes i have mail there, but i haven't give it when i installed postfix).
The second thing is in /var/log/mail.err:
> postfix/trivial-rewrite[8586]: fatal: mysql:/etc/postfix/mysql-virtual_domains.cf(0,lock|fold_fix): table lookup problem
Does anyone have any ideas for a solution?

---

### Post by martien on 2008-11-30
Ok, i followed another tutorial and it seems that it works. There are no errors in the mail.log. I tried to send mail using telnet and here is the log in /var/log/mail.log:
> Nov 30 22:34:11 stf postfix/smtpd[10283]: connect from localhost[127.0.0.1]
Nov 30 22:35:03 stf postfix/smtpd[10283]: 42DC4B022B: client=localhost[127.0.0.1]
Nov 30 22:35:13 stf postfix/cleanup[10305]: 42DC4B022B: message-id=<20081130203503.42DC4B022B@mail.[myserver]>
Nov 30 22:35:13 stf postfix/qmgr[10204]: 42DC4B022B: from=<webmaster@[mydomain]>, size=346, nrcpt=1 (queue active)
Nov 30 22:35:13 stf postfix/pipe[10307]: 42DC4B022B: to=<webmaster@[mydomain]>, relay=maildrop, delay=23, delays=23/0.01/0/0.02, dsn=2.0.0, status=sent (delivered via maildrop service)
Nov 30 22:35:13 stf postfix/qmgr[10204]: 42DC4B022B: removed
Nov 30 22:35:26 stf postfix/smtpd[10283]: disconnect from localhost[127.0.0.1]

but there is this line:
> Nov 30 22:35:13 stf postfix/qmgr[10204]: 42DC4B022B: removed
that i think it should be not showing. anyway /home/vmail/[mydomain]/webmaster/Maildir is empty and the mail is not sent.
EDIT: i found stored file /home/vmail/Maildir and there are the mails that i try to sent and recieve..
But i installed roundcube using apt-get and when i try to login to webmaster@[mydomain] it dies with php's 120 secs limit of execution.
Any ideas?

---

### Post by joenieburg on 2008-12-20
Can it be that the owner rights of your Maildir ar set to root instead off the user? U can see with ls -l in the users home dir

---

### Post by MJN on 2008-12-21
> **martien said:**
> but there is this line:

```
Nov 30 22:35:13 stf postfix/qmgr[10204]: 42DC4B022B: removed
```Don't worry about that - it is just saying the message has been removed from the queue as it has been dealt with.

> that i think it should be not showing. anyway /home/vmail/[mydomain]/webmaster/Maildir is empty and the mail is not sent.As you haven't told us where you were sending the message to, or your Postfix configuration, we can't really help you with this.

> EDIT: i found stored file /home/vmail/Maildir and there are the mails that i try to sent and recieve..Does that mean you don't have a problem now?

> But i installed roundcube using apt-get and when i try to login to webmaster@[mydomain] it dies with php's 120 secs limit of execution.Roundcube? You said you were using Squirrelmail? :confused:

We really need more information, much more.

Mathew

---

