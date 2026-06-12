---
title: "Postfix Connection Problem"
date: 2008-02-14
forum: Server Platforms
---

### Post by brooksbp on 2008-02-14
Hello I have a quick problem... So I followed all the guides for setting up Postfix... TLS... SMTP... POP and all that great stuff right...

But I can't connect via a Mail Client like OS X Mail or Thunderbird...

**Note:  I can send mail to the server: [email]brian@ncf.colorado.edu[/email] and login via ssh and read the mail... and reply via mailx and read the reply email from my other email address....

But just can't connect via POP.  I don't understand.

---

### Post by bmorency on 2008-02-14
to connect to your server you will need courier-pop (or courier-imap). that will allow you to connect to your server using an email client.

---

### Post by tcpip4lyfe on 2008-02-14
Do you get any error message when you try to connect to the pop server?

What do you get when you 

cat /var/log/mail.err
cat /var/log/mail.info
cat /var/log/mail.warn 
...etc?

---

### Post by brooksbp on 2008-02-14
I already installed courier-pop / courier-pop-ssl(?) and courier-imap / courier-imap-ssl(?) forgot if the packages were ssl or tls... but i installed them.... didn't do any configuration with them though... just apt-get'd them and restarted the server...

The error I get from OS X Mail is.... 

```
Trying to log into the POP server "ncf.colorado.edu" failed.  Make sure the user name and password you entered are correct, then click Continue."
```

I use the same login/passwd that I use to SSH into the server...  I use the server's domain name too... the server is ncf.colorado.edu so i put that as the Incoming Mail Server... or should that be mail.ncf.colorado.edu? But DNS isn't setup on the server so I wouldn't think so...

here's the output of the 3 cats

```
brian@www1:~$ cat /var/log/mail.err
Feb 14 13:27:28 www1 postfix[5019]: error: to submit mail, use the Postfix sendmail command
Feb 14 13:27:28 www1 postfix[5019]: fatal: the postfix command is reserved for the superuser
brian@www1:~$ cat /var/log/mail.info
Feb 14 13:13:58 www1 postfix/master[23313]: daemon started -- version 2.4.5, configuration /etc/postfix
Feb 14 13:14:08 www1 postfix/pickup[23315]: BB38689823B: uid=33 from=<www-data>
Feb 14 13:14:08 www1 postfix/cleanup[23323]: BB38689823B: message-id=<20080214201408.BB38689823B@www1>
Feb 14 13:14:08 www1 postfix/qmgr[23316]: BB38689823B: from=<www-data@www1>, size=279, nrcpt=1 (queue active)
Feb 14 13:14:08 www1 postfix/smtp[23325]: BB38689823B: to=<brian.brooks@colorado.edu>, relay=mx.colorado.edu[128.138.128.150]:25, delay=0.23, delays=0.02/0/0.21/0, dsn=5.0.0, status=bounced (host mx.colorado.edu[128.138.128.150] said: 504 Need Fully Qualified Address (in reply to MAIL FROM command))
Feb 14 13:14:09 www1 postfix/cleanup[23323]: 05B6A89823E: message-id=<20080214201409.05B6A89823E@www1>
Feb 14 13:14:09 www1 postfix/bounce[23326]: BB38689823B: sender non-delivery notification: 05B6A89823E
Feb 14 13:14:09 www1 postfix/qmgr[23316]: 05B6A89823E: from=<>, size=1985, nrcpt=1 (queue active)
Feb 14 13:14:09 www1 postfix/qmgr[23316]: BB38689823B: removed
Feb 14 13:14:09 www1 postfix/local[23327]: 05B6A89823E: to=<www-data@www1>, relay=local, delay=0.02, delays=0.01/0/0/0.01, dsn=2.0.0, status=sent (delivered to mailbox)
Feb 14 13:14:09 www1 postfix/qmgr[23316]: 05B6A89823E: removed
Feb 14 13:14:37 www1 postfix/master[23313]: terminating on signal 15
Feb 14 13:19:15 www1 postfix/master[4656]: daemon started -- version 2.4.5, configuration /etc/postfix
Feb 14 13:21:58 www1 postfix/master[4656]: terminating on signal 15
Feb 14 13:27:18 www1 postfix/master[5012]: daemon started -- version 2.4.5, configuration /etc/postfix
Feb 14 13:27:28 www1 postfix[5019]: error: to submit mail, use the Postfix sendmail command
Feb 14 13:27:28 www1 postfix[5019]: fatal: the postfix command is reserved for the superuser
Feb 14 13:27:38 www1 postfix/master[5012]: reload configuration /etc/postfix
Feb 14 13:28:40 www1 postfix/pickup[5031]: AE61A89823E: uid=33 from=<www-data>
Feb 14 13:28:40 www1 postfix/cleanup[5040]: AE61A89823E: message-id=<20080214202840.AE61A89823E@www1>
Feb 14 13:28:40 www1 postfix/qmgr[5030]: AE61A89823E: from=<www-data@ncf.colorado.edu>, size=291, nrcpt=1 (queue active)
Feb 14 13:28:40 www1 postfix/smtp[5042]: AE61A89823E: to=<brian.brooks@colorado.edu>, relay=mx.colorado.edu[128.138.128.150]:25, delay=0.25, delays=0.04/0.01/0.12/0.07, dsn=2.0.0, status=sent (250 Ok: queued as D7EB663B2D8)
Feb 14 13:28:40 www1 postfix/qmgr[5030]: AE61A89823E: removed
Feb 14 13:34:12 www1 postfix/smtpd[5053]: connect from smtp02.colorado.edu[128.138.128.142]
Feb 14 13:34:12 www1 postfix/smtpd[5053]: E1229898241: client=smtp02.colorado.edu[128.138.128.142]
Feb 14 13:34:12 www1 postfix/cleanup[5058]: E1229898241: message-id=<8D022236-C1AC-4671-A297-8B10AAA2A197@colorado.edu>
Feb 14 13:34:12 www1 postfix/smtpd[5053]: disconnect from smtp02.colorado.edu[128.138.128.142]
Feb 14 13:34:12 www1 postfix/qmgr[5030]: E1229898241: from=<Brian.Brooks@Colorado.EDU>, size=4116, nrcpt=1 (queue active)
Feb 14 13:34:12 www1 postfix/local[5059]: E1229898241: to=<brian@ncf.colorado.edu>, relay=local, delay=0.03, delays=0.02/0/0/0.01, dsn=2.0.0, status=sent (delivered to mailbox)
Feb 14 13:34:12 www1 postfix/qmgr[5030]: E1229898241: removed
Feb 14 13:37:32 www1 postfix/anvil[5056]: statistics: max connection rate 1/60s for (smtp:128.138.128.142) at Feb 14 13:34:12
Feb 14 13:37:32 www1 postfix/anvil[5056]: statistics: max connection count 1 for (smtp:128.138.128.142) at Feb 14 13:34:12
Feb 14 13:37:32 www1 postfix/anvil[5056]: statistics: max cache size 1 at Feb 14 13:34:12
Feb 14 14:01:58 www1 postfix/master[5012]: reload configuration /etc/postfix
Feb 14 14:08:23 www1 postfix/smtpd[5451]: connect from localhost[127.0.0.1]
Feb 14 14:09:10 www1 postfix/smtpd[5451]: disconnect from localhost[127.0.0.1]
Feb 14 14:11:20 www1 authdaemond: modules="authpam", daemons=5
Feb 14 14:11:20 www1 authdaemond: Installing libauthpam
Feb 14 14:11:20 www1 authdaemond: Installation complete: authpam
Feb 14 14:14:43 www1 pop3d-ssl: couriertls: connect: error:1408F10B:SSL routines:SSL3_GET_RECORD:wrong version number
Feb 14 14:15:43 www1 courierpop3login: chdir Maildir: No such file or directory
Feb 14 14:15:58 www1 pop3d-ssl: couriertls: accept: error:1408F10B:SSL routines:SSL3_GET_RECORD:wrong version number
Feb 14 14:16:28 www1 authdaemond: stopping authdaemond children
Feb 14 14:16:28 www1 postfix/master[5012]: terminating on signal 15
Feb 14 14:18:20 www1 authdaemond: modules="authpam", daemons=5
Feb 14 14:18:20 www1 authdaemond: Installing libauthpam
Feb 14 14:18:20 www1 authdaemond: Installation complete: authpam
Feb 14 14:18:20 www1 postfix/master[4633]: daemon started -- version 2.4.5, configuration /etc/postfix
Feb 14 14:20:30 www1 pop3d-ssl: couriertls: connect: error:1408F10B:SSL routines:SSL3_GET_RECORD:wrong version number
Feb 14 14:21:30 www1 courierpop3login: chdir Maildir: No such file or directory
Feb 14 14:22:26 www1 pop3d-ssl: couriertls: accept: error:1408F10B:SSL routines:SSL3_GET_RECORD:wrong version number
Feb 14 14:23:26 www1 courierpop3login: chdir Maildir: No such file or directory
brian@www1:~$ cat /var/log/mail.warn
Feb 14 13:27:28 www1 postfix[5019]: error: to submit mail, use the Postfix sendmail command
Feb 14 13:27:28 www1 postfix[5019]: fatal: the postfix command is reserved for the superuser

```

---

### Post by brooksbp on 2008-02-14
I should also mention that I have the OS X Mail account setup and the SMTP server setup in the client...

and I can send email via SMTP... I just can't read from POP or IMAP or anything...

---

### Post by tcpip4lyfe on 2008-02-14
The ssh username and password won't work for pop server login.  You're going to have to find out how to add a new user in courier.  Im not sure off the top pf my head how to do that.  I've always cheated and used webmin.

---

