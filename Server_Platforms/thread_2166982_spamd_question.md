---
title: "spamd question"
date: 2013-08-11
forum: Server Platforms
---

### Post by nerdtron on 2013-08-11
Hi all,
In our old mail server. I was looking at the logs and trying to find out 1 lost email.
```
Jul 12 16:56:45 mail msd[9436]: Initializing for connection from 209.85.214.47
Jul 12 16:56:45 mail msd[9436]: EHLO command received, args: mail-bk0-f47.google.com
Jul 12 16:56:45 mail msd[9436]: HELO host does not match TCPREMOTEHOST
Jul 12 16:56:47 mail msd[9436]: MAIL command received, args: FROM:<jmalguso@sender.ph>
Jul 12 16:56:47 mail msd[9436]: rcpthost [sender.ph] matched [sender.ph]
Jul 12 16:56:47 mail msd[9437]: running external check user program: [/var/qmail/bin/vpopmail-check-user.sh] [jmalguso@sender.ph] 
Jul 12 16:56:47 mail msd[9436]: Allowed to relay: no
Jul 12 16:56:47 mail msd[9436]: rcpthost [ourdomain.com.ph] matched [ourdomain.com.ph]
Jul 12 16:56:47 mail msd[9446]: running external check user program: [/var/qmail/bin/vpopmail-check-user.sh] [ed@ourdomain.com.ph] 
Jul 12 16:56:47 mail msd[9436]: RCPT command received (209.85.214.47), args: ed@ourdomain.com.ph (local/exist)
Jul 12 16:56:47 mail msd[9436]: config_spam_rule_load() took 0.000004 seconds 
Jul 12 16:56:47 mail msd[9436]: retval = 1
Jul 12 16:56:47 mail msd[9436]: DATA command received, args: 
Jul 12 16:56:47 mail msd[9436]: incrementing hop count
Jul 12 16:56:47 mail msd[9436]: incrementing hop count
Jul 12 16:57:04 mail msd[9436]: Returning 250 ok [qp 9455] for data
Jul 12 16:57:04 mail msd[9436]: QUIT command received, args: 
Jul 12 16:57:04 mail msd[9436]: Exiting


```

I believe we have spamd running in the background. 
```
[root@mail ~]# ps -ef | grep spam
root      2102     1  0 09:29 ?        00:00:01 /usr/bin/spamd -x -u spamd -H /home/spamd -d -r /var/run/spamd.pid
spamd     2164  2102  0 09:29 ?        00:00:00 spamd child
spamd     2167  2102  0 09:29 ?        00:00:00 spamd child
vpopmail  2534  2528  0 09:30 ?        00:00:00 /usr/local/bin/tcpserver -v -H -R -l mail.apolloglobal.net -x /etc/tcp.smtp.cdb -c 30 -u 507 -g 502 0 smtp rblsmtpd -r zen.spamhaus.org -r bl.spamcop.net /var/qmail/bin/qmail-smtpd mail.apolloglobal.net /home/vpopmail/bin/vchkpw /usr/bin/true
root      3347  3006  0 09:55 pts/2    00:00:00 grep spam


```
I was not the original administrator for this server so I was not very sure about how he configured this server.
Anyway, my question is this. What does this mean?
```
Jul 12 16:56:47 mail msd[9436]: config_spam_rule_load() took 0.000004 seconds 
Jul 12 16:56:47 mail msd[9436]: retval = 1
```
Does it mean that the email was mark as spam and not relayed to the recipient?
I'm not sure if retval = 1 means "this email is marked as spam" or "this email is good, you should pass".
Any thoughts?

---

