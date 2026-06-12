---
title: "Postfix Maildir problem"
date: 2008-04-14
forum: Server Platforms
---

### Post by refdoc on 2008-04-14
I installed postfix on Ubuntu 7.10

If I leave in /etc/main.cf the directive re home_mailbox on default, all email goes into /var/spool/mail/$USER mbox formatted.

If I add a 

home_mailbox = Maildir/

to main.cf I start to get error messages

Apr 14 13:10:29 serv2 postfix/qmgr[11039]: 06BD2F1C085: to=<administrator@serv2.mydomain.com>, relay=none, delay=1329, delays=1328/1.1/0/0, dsn=4.3.0, status=deferred (unknown mail transport error)

I have a Maildir in every /home/$USER



I tried to "unchroot" the postfix smtp and the qmgr processes to see if this makes 
a difference, but it does not.

I have tried to create a INBOX Maildir within /user/home/$USER  - no joy.

I have created a Maildir at /var/spool/mail/$USER - no joy.


I checked the Ubuntu wiki and it appears my settings are as they should be. I checked here and found a single thread referring to my problem, but it was without answer. 

What am I doing wrong?

---

### Post by MJN on 2008-04-14
Check your logs, not just around the point of sending a message but right from when Postfix is restarted. In particularl look out for anything serious that could indicate what is wrong. Post the full log (again, from a Postfix restart) if you are unsure.
 
Mathew

---

### Post by refdoc on 2008-04-14
Ok, this is the log when everything goes into an mbox - as you see the test message goes in fine.

Apr 14 13:46:58 serv2 postfix/smtpd[11590]: connect from smtp.sender.com[a.b.c.d]
Apr 14 13:46:59 serv2 postfix/smtpd[11590]: 0087EF1C08B: client=smtp.sender.com[a.b.c.d]
Apr 14 13:46:59 serv2 postfix/cleanup[11593]: 0087EF1C08B: message-id=<48035329.9040606@smtp.sender.com>
Apr 14 13:46:59 serv2 postfix/qmgr[11540]: 0087EF1C08B: from=<me@smtp.sender.com>, size=2825, nrcpt=1 (queue active)
Apr 14 13:46:59 serv2 postfix/local[11594]: 0087EF1C08B: to=<administrator@mydomain.com>, relay=local, delay=0.15, delays=0.12/0.01/0/0.02, dsn=2.0.0, status=sent (delivered to mailbox)
Apr 14 13:46:59 serv2 postfix/qmgr[11540]: 0087EF1C08B: removed

I now add the directive home_mailbox= Maildir/ and restart + send another test message. Nothing else done. Here is the complete maillog: 

Apr 14 13:52:17 serv2 postfix/master[11694]: daemon started -- version 2.3.3, configuration /etc/postfix
Apr 14 13:52:40 serv2 postfix/smtpd[11700]: connect from smtp.sender.com[a.b.c.d]
Apr 14 13:52:40 serv2 postfix/smtpd[11700]: CAB1BF1C086: client=smtp.sender.com[a.b.c.d]
Apr 14 13:52:40 serv2 postfix/cleanup[11705]: CAB1BF1C086: message-id=<48035482.7090609@smtp.sender.com>
Apr 14 13:52:40 serv2 postfix/qmgr[11699]: CAB1BF1C086: from=<me@smtp.sender.com>, size=2831, nrcpt=1 (queue active)
Apr 14 13:52:40 serv2 postfix/local[11706]: fatal: gethostbyname: Success
Apr 14 13:52:41 serv2 postfix/smtpd[11700]: disconnect from smtp.sender.com[a.b.c.d]
Apr 14 13:52:41 serv2 postfix/qmgr[11699]: warning: premature end-of-input on private/local socket while reading input attribute name
Apr 14 13:52:41 serv2 postfix/qmgr[11699]: warning: private/local socket: malformed response
Apr 14 13:52:41 serv2 postfix/qmgr[11699]: warning: transport local failure -- see a previous warning/fatal/panic logfile record for the problem description
Apr 14 13:52:41 serv2 postfix/master[11694]: warning: process /usr/lib/postfix/local pid 11706 exit status 1
Apr 14 13:52:41 serv2 postfix/master[11694]: warning: /usr/lib/postfix/local: bad command startup -- throttling
Apr 14 13:52:41 serv2 postfix/qmgr[11699]: CAB1BF1C086: to=<administrator@mydomain.com>, relay=none, delay=1.2, delays=0.12/1.1/0/0, dsn=4.3.0, status=deferred (unknown mail transport error)

---

### Post by refdoc on 2008-04-14
And this is /var/log/mail.err


Apr 14 13:52:40 serv2 postfix/local[11706]: fatal: gethostbyname: Success

this is /var/log/mail.info

Apr 14 13:52:41 serv2 postfix/qmgr[11699]: warning: premature end-of-input on private/local socket while reading input attribute name
Apr 14 13:52:41 serv2 postfix/qmgr[11699]: warning: private/local socket: malformed response
Apr 14 13:52:41 serv2 postfix/qmgr[11699]: warning: transport local failure -- see a previous warning/fatal/panic logfile record for the problem description
Apr 14 13:52:41 serv2 postfix/master[11694]: warning: process /usr/lib/postfix/local pid 11706 exit status 1
Apr 14 13:52:41 serv2 postfix/master[11694]: warning: /usr/lib/postfix/local: bad command startup -- throttling
Apr 14 13:52:41 serv2 postfix/qmgr[11699]: CAB1BF1C086: to=<administrator@mydomain.com>, relay=none, delay=1.2, delays=0.12/1.1/0/0, dsn=4.3.0, status=deferred (unknown mail transport error)

Thanks!

---

### Post by refdoc on 2008-04-14
The whole lot of error messages posted above will only come when a mail actually tried to get through.

Simply starting up postfix with /etc/init.d/postfix restart will not resuit in any error messages

---

### Post by MJN on 2008-04-14
It looks like you are having DNS name resolution issues, either due to your chroot environment or problems with your hostname. Regarding the latter, is your /etc/hosts file all set up correctly and does it match whatever hostname is specified in Postfix? (also see what hosthame -f gives)
 
Mathew

---

### Post by refdoc on 2008-04-14
Thanks a lot!!!

There was indeed a mismatch between /etc/hostname and the localhost declarations in /etc/hosts


That was all there was to it.

---

### Post by MJN on 2008-04-14
Excellent.
 
Remember, the logs are there for your benefit - and whenever a word like 'fatal' is used then it pays to find out why! ;)
 
Mathew

---

