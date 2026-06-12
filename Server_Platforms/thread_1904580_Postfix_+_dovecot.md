---
title: "Postfix + dovecot"
date: 2012-01-05
forum: Server Platforms
---

### Post by dazman19 on 2012-01-05
Hey,

I am setting up my first linux mail server ever and to be quite honest i am a bit lost.

Its a debian box. so i followed this tutorial: 
[http://www.debianadmin.com/debian-mail-server-setup-with-postfix-dovecot-sasl-squirrel-mail.html](http://www.debianadmin.com/debian-mail-server-setup-with-postfix-dovecot-sasl-squirrel-mail.html)

i can send email from the localhost to accounts i have created on the localhost.. but i dont have a clue on how to connect it to the relay server so i can send emails over the web. How do i do this?

Also when i try to connect with thunderbird i get certificate problems.

here are them mail messages 
This one worked... 

Message 4:
From [email]daz@bacon.net.nz[/email]  Thu Jan  5 19:22:28 2012
X-Original-To: [email]daz@bacon.net.nz[/email]
To: [email]daz@bacon.net.nz[/email], "to:"@bacon.net.nz
Subject: test email
Date: Thu,  5 Jan 2012 19:22:27 +1300 (NZDT)
From: [email]daz@bacon.net.nz[/email] (daz)

some text blah
test 123

Most of them are like this:

From MAILER-DAEMON  Thu Jan  5 19:00:31 2012
X-Original-To: [email]daz@bacon.net.nz[/email]
Date: Thu,  5 Jan 2012 19:00:31 +1300 (NZDT)
From: [email]MAILER-DAEMON@bacon.net.nz[/email] (Mail Delivery System)
Subject: Undelivered Mail Returned to Sender
To: [email]daz@bacon.net.nz[/email]
Auto-Submitted: auto-replied
MIME-Version: 1.0
Content-Type: multipart/report; report-type=delivery-status;
        boundary="0E6561C5CC9.1325743231/daz-laptop.daz-laptop"

This is a MIME-encapsulated message.

--0E6561C5CC9.1325743231/daz-laptop.daz-laptop
Content-Description: Notification
Content-Type: text/plain; charset=us-ascii

This is the mail system at host daz-laptop.daz-laptop.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

i dont really know where to go from here. And i have certificate issues with thunderbird so i cant send mail out.

I only really want a SMTP authentication server set up to use my mail-relay server can anyone point me in the right direction?

---

### Post by balagosa on 2012-01-05
try to post the output of mail logs.

tail -n 100 /var/log/maillog

---

### Post by dazman19 on 2012-01-05
this is what i have (last 100 lines)

Jan  5 18:59:09 daz-laptop dovecot: Killed with signal 15 (by pid=30986 uid=0 code=kill)
Jan  5 18:59:09 daz-laptop dovecot: Dovecot v1.2.15 starting up (core dumps disabled)
Jan  5 19:00:25 daz-laptop postfix/pickup[30287]: 0E6561C5CC9: uid=1000 from=<daz>
Jan  5 19:00:25 daz-laptop postfix/cleanup[31011]: 0E6561C5CC9: message-id=<20120105060025.0E6561C5CC9@daz-laptop.daz-laptop>
Jan  5 19:00:25 daz-laptop postfix/qmgr[30288]: 0E6561C5CC9: from=<daz@bacon.net.nz>, size=353, nrcpt=2 (queue active)
Jan  5 19:00:25 daz-laptop postfix/local[31014]: 0E6561C5CC9: to=<to:@bacon.net.nz>, orig_to=<to:>, relay=local, delay=0.44, delays=0.36/0.01/0/0.08, dsn=5.1.1, status=bounced (unknown user: "to:")
Jan  5 19:00:31 daz-laptop postfix/smtp[31013]: 0E6561C5CC9: to=<darylblake@gmail.com>, relay=gmail-smtp-in.l.google.com[74.125.65.26]:25, delay=6.6, delays=0.36/0.01/2.1/4.1, dsn=2.0.0, status=sent (250 2.0.0 OK 1325743479 i14si1622995ann.148)
Jan  5 19:00:31 daz-laptop postfix/cleanup[31011]: 6098B1C5CCD: message-id=<20120105060031.6098B1C5CCD@daz-laptop.daz-laptop>
Jan  5 19:00:31 daz-laptop postfix/bounce[31015]: 0E6561C5CC9: sender non-delivery notification: 6098B1C5CCD
Jan  5 19:00:31 daz-laptop postfix/qmgr[30288]: 6098B1C5CCD: from=<>, size=2171, nrcpt=1 (queue active)
Jan  5 19:00:31 daz-laptop postfix/qmgr[30288]: 0E6561C5CC9: removed
Jan  5 19:00:31 daz-laptop postfix/local[31014]: 6098B1C5CCD: to=<daz@bacon.net.nz>, relay=local, delay=0.28, delays=0.18/0/0/0.09, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Jan  5 19:00:31 daz-laptop postfix/qmgr[30288]: 6098B1C5CCD: removed
Jan  5 19:03:34 daz-laptop dovecot: imap-login: Aborted login (no auth attempts): rip=192.168.178.2, lip=192.168.178.3
Jan  5 19:03:35 daz-laptop postfix/smtpd[31039]: connect from unknown[192.168.178.2]
Jan  5 19:03:35 daz-laptop postfix/smtpd[31043]: connect from unknown[192.168.178.2]
Jan  5 19:03:35 daz-laptop postfix/smtpd[31043]: improper command pipelining after EHLO from unknown[192.168.178.2]
Jan  5 19:03:35 daz-laptop postfix/smtpd[31043]: disconnect from unknown[192.168.178.2]
Jan  5 19:03:35 daz-laptop postfix/smtpd[31039]: disconnect from unknown[192.168.178.2]
Jan  5 19:03:37 daz-laptop dovecot: imap-login: Aborted login (no auth attempts): rip=192.168.178.2, lip=192.168.178.3
Jan  5 19:03:37 daz-laptop dovecot: imap-login: Disconnected (no auth attempts): rip=192.168.178.2, lip=192.168.178.3, TLS handshaking: SSL_accept() failed: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Jan  5 19:03:37 daz-laptop dovecot: imap-login: Aborted login (no auth attempts): rip=192.168.178.2, lip=192.168.178.3, TLS
Jan  5 19:04:03 daz-laptop dovecot: imap-login: Disconnected (no auth attempts): rip=192.168.178.2, lip=192.168.178.3, TLS handshaking: SSL_accept() failed: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Jan  5 19:04:04 daz-laptop dovecot: imap-login: Disconnected (no auth attempts): rip=192.168.178.2, lip=192.168.178.3, TLS handshaking: SSL_accept() failed: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Jan  5 19:04:05 daz-laptop dovecot: imap-login: Aborted login (no auth attempts): rip=192.168.178.2, lip=192.168.178.3
Jan  5 19:04:05 daz-laptop postfix/smtpd[31043]: connect from unknown[192.168.178.2]
Jan  5 19:04:05 daz-laptop postfix/smtpd[31039]: connect from unknown[192.168.178.2]
Jan  5 19:04:05 daz-laptop postfix/smtpd[31043]: disconnect from unknown[192.168.178.2]
Jan  5 19:04:05 daz-laptop postfix/smtpd[31039]: lost connection after UNKNOWN from unknown[192.168.178.2]
Jan  5 19:04:05 daz-laptop postfix/smtpd[31039]: disconnect from unknown[192.168.178.2]
Jan  5 19:04:05 daz-laptop postfix/smtpd[31052]: connect from unknown[192.168.178.2]
Jan  5 19:04:05 daz-laptop postfix/smtpd[31052]: lost connection after CONNECT from unknown[192.168.178.2]
Jan  5 19:04:05 daz-laptop postfix/smtpd[31052]: disconnect from unknown[192.168.178.2]
Jan  5 19:04:09 daz-laptop dovecot: imap-login: Disconnected (no auth attempts): rip=192.168.178.2, lip=192.168.178.3, TLS handshaking: SSL_accept() failed: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Jan  5 19:04:10 daz-laptop dovecot: imap-login: Disconnected (no auth attempts): rip=192.168.178.2, lip=192.168.178.3, TLS handshaking: SSL_accept() failed: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Jan  5 19:04:28 daz-laptop dovecot: imap-login: Login: user=<daryl>, method=PLAIN, rip=192.168.178.2, lip=192.168.178.3
Jan  5 19:04:28 daz-laptop dovecot: IMAP(daryl): mail_location not set and autodetection failed: Mail storage autodetection failed with home=/home/daryl
Jan  5 19:04:28 daz-laptop dovecot: IMAP(daryl): Fatal: Namespace initialization failed
Jan  5 19:04:28 daz-laptop dovecot: imap-login: Login: user=<daryl>, method=PLAIN, rip=192.168.178.2, lip=192.168.178.3
Jan  5 19:04:28 daz-laptop dovecot: IMAP(daryl): mail_location not set and autodetection failed: Mail storage autodetection failed with home=/home/daryl
Jan  5 19:04:28 daz-laptop dovecot: IMAP(daryl): Fatal: Namespace initialization failed
Jan  5 19:04:51 daz-laptop dovecot: imap-login: Disconnected (auth failed, 2 attempts): user=<daryl@bacon.net.nz>, method=PLAIN, rip=192.168.178.2, lip=192.168.178.3
Jan  5 19:04:54 daz-laptop dovecot: imap-login: Aborted login (no auth attempts): rip=192.168.178.2, lip=192.168.178.3
Jan  5 19:04:54 daz-laptop dovecot: imap-login: Aborted login (no auth attempts): rip=192.168.178.2, lip=192.168.178.3
Jan  5 19:04:54 daz-laptop postfix/smtpd[31043]: connect from unknown[192.168.178.2]
Jan  5 19:04:54 daz-laptop postfix/smtpd[31039]: connect from unknown[192.168.178.2]
Jan  5 19:04:54 daz-laptop postfix/smtpd[31039]: improper command pipelining after EHLO from unknown[192.168.178.2]
Jan  5 19:04:54 daz-laptop postfix/smtpd[31039]: disconnect from unknown[192.168.178.2]
Jan  5 19:04:54 daz-laptop dovecot: imap-login: Disconnected (no auth attempts): rip=192.168.178.2, lip=192.168.178.3, TLS handshaking: SSL_accept() failed: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Jan  5 19:04:54 daz-laptop postfix/smtpd[31043]: improper command pipelining after EHLO from unknown[192.168.178.2]
Jan  5 19:04:54 daz-laptop postfix/smtpd[31043]: disconnect from unknown[192.168.178.2]
Jan  5 19:04:54 daz-laptop dovecot: imap-login: Aborted login (no auth attempts): rip=192.168.178.2, lip=192.168.178.3, TLS
Jan  5 19:08:14 daz-laptop postfix/anvil[31044]: statistics: max connection rate 5/60s for (smtp:192.168.178.2) at Jan  5 19:04:05
Jan  5 19:08:14 daz-laptop postfix/anvil[31044]: statistics: max connection count 2 for (smtp:192.168.178.2) at Jan  5 19:03:35
Jan  5 19:08:14 daz-laptop postfix/anvil[31044]: statistics: max cache size 1 at Jan  5 19:03:35
Jan  5 19:18:03 daz-laptop postfix/master[30281]: terminating on signal 15
Jan  5 19:18:03 daz-laptop postfix/master[31267]: daemon started -- version 2.7.1, configuration /etc/postfix
Jan  5 19:18:15 daz-laptop dovecot: dovecot: Killed with signal 15 (by pid=31287 uid=0 code=kill)
Jan  5 19:18:15 daz-laptop dovecot: Dovecot v1.2.15 starting up (core dumps disabled)
Jan  5 19:19:29 daz-laptop postfix/smtpd[31311]: connect from unknown[192.168.178.2]
Jan  5 19:19:29 daz-laptop postfix/smtpd[31314]: connect from unknown[192.168.178.2]
Jan  5 19:19:29 daz-laptop postfix/smtpd[31311]: improper command pipelining after EHLO from unknown[192.168.178.2]
Jan  5 19:19:29 daz-laptop postfix/smtpd[31311]: disconnect from unknown[192.168.178.2]
Jan  5 19:19:32 daz-laptop dovecot: imap-login: Aborted login (no auth attempts): rip=192.168.178.2, lip=192.168.178.3
Jan  5 19:19:32 daz-laptop postfix/smtpd[31311]: connect from unknown[192.168.178.2]
Jan  5 19:19:32 daz-laptop postfix/smtpd[31311]: improper command pipelining after EHLO from unknown[192.168.178.2]
Jan  5 19:19:32 daz-laptop postfix/smtpd[31311]: disconnect from unknown[192.168.178.2]
Jan  5 19:19:32 daz-laptop postfix/smtpd[31314]: lost connection after UNKNOWN from unknown[192.168.178.2]
Jan  5 19:19:32 daz-laptop postfix/smtpd[31314]: disconnect from unknown[192.168.178.2]
Jan  5 19:19:35 daz-laptop dovecot: imap-login: Disconnected (no auth attempts): rip=192.168.178.2, lip=192.168.178.3, TLS handshaking: SSL_accept() failed: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Jan  5 19:19:36 daz-laptop dovecot: imap-login: Disconnected (no auth attempts): rip=192.168.178.2, lip=192.168.178.3, TLS handshaking: SSL_accept() failed: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Jan  5 19:19:50 daz-laptop dovecot: imap-login: Disconnected (no auth attempts): rip=192.168.178.2, lip=192.168.178.3, TLS handshaking: SSL_accept() failed: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Jan  5 19:19:50 daz-laptop dovecot: imap-login: Disconnected (no auth attempts): rip=192.168.178.2, lip=192.168.178.3, TLS handshaking: SSL_accept() failed: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Jan  5 19:20:12 daz-laptop dovecot: imap-login: Disconnected (no auth attempts): rip=192.168.178.2, lip=192.168.178.3, TLS handshaking: SSL_accept() failed: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Jan  5 19:20:12 daz-laptop dovecot: imap-login: Disconnected (no auth attempts): rip=192.168.178.2, lip=192.168.178.3, TLS handshaking: SSL_accept() failed: error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca
Jan  5 19:21:29 daz-laptop postfix/pickup[31273]: 241251C5CD0: uid=1000 from=<daz>
Jan  5 19:21:29 daz-laptop postfix/cleanup[31350]: 241251C5CD0: message-id=<20120105062129.241251C5CD0@daz-laptop.daz-laptop>
Jan  5 19:21:29 daz-laptop postfix/qmgr[31274]: 241251C5CD0: from=<daz@bacon.net.nz>, size=332, nrcpt=2 (queue active)
Jan  5 19:21:29 daz-laptop postfix/local[31353]: 241251C5CD0: to=<to:@bacon.net.nz>, orig_to=<to:>, relay=local, delay=0.22, delays=0.15/0.01/0/0.07, dsn=5.1.1, status=bounced (unknown user: "to:")
Jan  5 19:21:32 daz-laptop postfix/smtp[31352]: 241251C5CD0: to=<darylblake@gmail.com>, relay=gmail-smtp-in.l.google.com[74.125.65.27]:25, delay=3.8, delays=0.15/0.01/2.1/1.6, dsn=2.0.0, status=sent (250 2.0.0 OK 1325744741 d37si25359894anp.189)
Jan  5 19:21:32 daz-laptop postfix/cleanup[31350]: DFAC21C5CD1: message-id=<20120105062132.DFAC21C5CD1@daz-laptop.daz-laptop>
Jan  5 19:21:32 daz-laptop postfix/bounce[31354]: 241251C5CD0: sender non-delivery notification: DFAC21C5CD1
Jan  5 19:21:32 daz-laptop postfix/qmgr[31274]: DFAC21C5CD1: from=<>, size=2150, nrcpt=1 (queue active)
Jan  5 19:21:32 daz-laptop postfix/qmgr[31274]: 241251C5CD0: removed
Jan  5 19:21:33 daz-laptop postfix/local[31353]: DFAC21C5CD1: to=<daz@bacon.net.nz>, relay=local, delay=0.14, delays=0.06/0/0/0.08, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Jan  5 19:21:33 daz-laptop postfix/qmgr[31274]: DFAC21C5CD1: removed
Jan  5 19:22:28 daz-laptop postfix/pickup[31273]: 16E871C5CD0: uid=1000 from=<daz>
Jan  5 19:22:28 daz-laptop postfix/cleanup[31350]: 16E871C5CD0: message-id=<20120105062228.16E871C5CD0@daz-laptop.daz-laptop>
Jan  5 19:22:28 daz-laptop postfix/qmgr[31274]: 16E871C5CD0: from=<daz@bacon.net.nz>, size=354, nrcpt=2 (queue active)
Jan  5 19:22:28 daz-laptop postfix/local[31353]: 16E871C5CD0: to=<daz@bacon.net.nz>, relay=local, delay=0.47, delays=0.4/0/0/0.07, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Jan  5 19:22:28 daz-laptop postfix/local[31364]: 16E871C5CD0: to=<to:@bacon.net.nz>, orig_to=<to:>, relay=local, delay=0.53, delays=0.4/0.01/0/0.12, dsn=5.1.1, status=bounced (unknown user: "to:")
Jan  5 19:22:28 daz-laptop postfix/cleanup[31350]: 46A2E1C5CD1: message-id=<20120105062228.46A2E1C5CD1@daz-laptop.daz-laptop>
Jan  5 19:22:28 daz-laptop postfix/bounce[31354]: 16E871C5CD0: sender non-delivery notification: 46A2E1C5CD1
Jan  5 19:22:28 daz-laptop postfix/qmgr[31274]: 46A2E1C5CD1: from=<>, size=2172, nrcpt=1 (queue active)
Jan  5 19:22:28 daz-laptop postfix/qmgr[31274]: 16E871C5CD0: removed
Jan  5 19:22:28 daz-laptop postfix/local[31353]: 46A2E1C5CD1: to=<daz@bacon.net.nz>, relay=local, delay=0.12, delays=0.05/0/0/0.07, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Jan  5 19:22:28 daz-laptop postfix/qmgr[31274]: 46A2E1C5CD1: removed
Jan  5 19:22:52 daz-laptop postfix/anvil[31315]: statistics: max connection rate 3/60s for (smtp:192.168.178.2) at Jan  5 19:19:32
Jan  5 19:22:52 daz-laptop postfix/anvil[31315]: statistics: max connection count 2 for (smtp:192.168.178.2) at Jan  5 19:19:29
Jan  5 19:22:52 daz-laptop postfix/anvil[31315]: statistics: max cache size 1 at Jan  5 19:19:29

---

