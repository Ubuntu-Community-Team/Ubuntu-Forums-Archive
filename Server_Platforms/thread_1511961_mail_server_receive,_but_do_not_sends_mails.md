---
title: "mail server receive, but do not sends mails"
date: 2010-06-17
forum: Server Platforms
---

### Post by attila-farkas on 2010-06-17
Hi, i installed and configured a mail server on my ubuntu 9,04 as described in this guide:
[https://help.ubuntu.com/community/MailServer]("https://help.ubuntu.com/community/MailServer") where MTA is postfix and MDA is dovecot, and connected to net via dyndns.com ... the server is receiving mails, but is unable to send them...

when sending, there is no error message, but mails never arive to recipients ...

here is the content of my /var/log/mail.log :

```
Jun 10 21:28:27 attila-asus postfix/master[8999]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 10 21:28:30 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 10 21:28:30 attila-asus dovecot: Generating Diffie-Hellman parameters for the first time. This may take a while..
Jun 10 21:28:31 attila-asus dovecot: Killed with signal 15
Jun 10 21:28:31 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 10 21:28:31 attila-asus dovecot: Generating Diffie-Hellman parameters for the first time. This may take a while..
Jun 10 21:28:31 attila-asus dovecot: Killed with signal 15
Jun 10 21:28:31 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 10 21:28:31 attila-asus dovecot: Generating Diffie-Hellman parameters for the first time. This may take a while..
Jun 10 21:30:02 attila-asus postfix/master[8999]: terminating on signal 15
Jun 10 21:31:06 attila-asus postfix/master[2765]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 10 21:31:07 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 10 21:31:17 attila-asus postfix/master[2765]: reload configuration /etc/postfix
Jun 10 22:14:58 attila-asus postfix/master[2765]: terminating on signal 15
Jun 10 23:11:44 attila-asus postfix/master[2758]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 10 23:11:45 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 10 23:11:56 attila-asus postfix/master[2758]: reload configuration /etc/postfix
Jun 11 00:11:13 attila-asus postfix/master[2758]: terminating on signal 15
Jun 11 06:32:05 attila-asus postfix/master[2771]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 11 06:32:05 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 11 06:32:16 attila-asus postfix/master[2771]: reload configuration /etc/postfix
Jun 11 07:20:57 attila-asus postfix/master[2771]: terminating on signal 15
Jun 11 15:55:58 attila-asus postfix/master[2766]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 11 15:55:58 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 11 15:56:08 attila-asus postfix/master[2766]: reload configuration /etc/postfix
Jun 11 16:28:23 attila-asus postfix/master[2766]: terminating on signal 15
Jun 11 16:29:22 attila-asus postfix/master[2775]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 11 16:29:23 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 11 16:29:34 attila-asus postfix/master[2775]: reload configuration /etc/postfix
Jun 11 16:35:48 attila-asus postfix/master[2775]: terminating on signal 15
Jun 11 16:36:47 attila-asus postfix/master[2773]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 11 16:36:48 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 11 16:36:56 attila-asus postfix/master[2773]: reload configuration /etc/postfix
Jun 11 16:44:38 attila-asus postfix/master[2773]: terminating on signal 15
Jun 11 16:45:35 attila-asus postfix/master[2777]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 11 16:45:36 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 11 16:45:46 attila-asus postfix/master[2777]: reload configuration /etc/postfix
Jun 13 14:16:00 attila-asus postfix/master[2779]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 13 14:16:01 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 13 14:16:09 attila-asus postfix/master[2779]: reload configuration /etc/postfix
Jun 13 14:40:04 attila-asus postfix/pickup[3507]: 97FEF221D: uid=0 from=<root>
Jun 13 14:40:04 attila-asus postfix/cleanup[5282]: 97FEF221D: message-id=<20100613124004.97FEF221D@attila-asus>
Jun 13 14:40:04 attila-asus postfix/qmgr[3509]: 97FEF221D: from=<root@attila-farkas.homelinux.com>, size=484, nrcpt=1 (queue active)
Jun 13 14:40:05 attila-asus postfix/local[5284]: 97FEF221D: to=<root@attila-farkas.homelinux.com>, orig_to=<root>, relay=local, delay=1.3, delays=0.17/0.05/0/1.1, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Jun 13 14:40:05 attila-asus postfix/qmgr[3509]: 97FEF221D: removed
Jun 16 17:42:52 attila-asus postfix/master[2793]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 16 17:42:52 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 16 17:43:00 attila-asus postfix/master[2793]: reload configuration /etc/postfix
Jun 16 17:57:45 attila-asus postfix/master[2793]: terminating on signal 15
Jun 16 18:00:52 attila-asus postfix/master[5246]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 16 18:05:18 attila-asus postfix/master[5246]: terminating on signal 15
Jun 16 18:05:19 attila-asus postfix/master[5401]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 16 18:10:32 attila-asus postfix/master[5401]: terminating on signal 15
Jun 16 18:10:33 attila-asus postfix/master[5959]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 16 18:10:52 attila-asus postfix/smtpd[5967]: warning: database /etc/aliases.db is older than source file /etc/aliases
Jun 16 18:10:53 attila-asus postfix/smtpd[5967]: warning: ::1: address not listed for hostname localhost
Jun 16 18:10:53 attila-asus postfix/smtpd[5967]: connect from unknown[::1]
Jun 16 18:11:21 attila-asus postfix/smtpd[5967]: disconnect from unknown[::1]
Jun 16 18:20:08 attila-asus postfix/master[5959]: terminating on signal 15
Jun 16 18:20:08 attila-asus postfix/master[6398]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 16 18:27:12 attila-asus postfix/smtpd[7358]: warning: database /etc/aliases.db is older than source file /etc/aliases
Jun 16 18:27:12 attila-asus postfix/smtpd[7358]: warning: ::1: address not listed for hostname localhost
Jun 16 18:27:12 attila-asus postfix/smtpd[7358]: connect from unknown[::1]
Jun 16 18:27:47 attila-asus postfix/smtpd[7358]: disconnect from unknown[::1]
Jun 16 18:30:14 attila-asus postfix/master[6398]: terminating on signal 15
Jun 16 18:30:14 attila-asus postfix/master[7706]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 16 18:30:49 attila-asus postfix/smtpd[7743]: warning: database /etc/aliases.db is older than source file /etc/aliases
Jun 16 18:30:49 attila-asus postfix/smtpd[7743]: warning: ::1: address not listed for hostname localhost
Jun 16 18:30:49 attila-asus postfix/smtpd[7743]: connect from unknown[::1]
Jun 16 18:31:07 attila-asus postfix/smtpd[7743]: disconnect from unknown[::1]
Jun 16 18:44:35 attila-asus dovecot: pop3-login: Aborted login (no auth attempts): rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:46:03 attila-asus dovecot: imap-login: Disconnected (no auth attempts): rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:56:16 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:56:16 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=44/298
Jun 16 18:56:17 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:56:17 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=417/1317
Jun 16 18:56:17 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:56:17 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=117/931
Jun 16 18:56:34 attila-asus postfix/smtpd[8659]: warning: database /etc/aliases.db is older than source file /etc/aliases
Jun 16 18:56:34 attila-asus postfix/smtpd[8659]: warning: ::1: address not listed for hostname localhost
Jun 16 18:56:34 attila-asus postfix/smtpd[8659]: connect from unknown[::1]
Jun 16 18:56:34 attila-asus postfix/smtpd[8659]: C606F1D16: client=unknown[::1]
Jun 16 18:56:34 attila-asus postfix/cleanup[8662]: C606F1D16: message-id=<56820abcaa5640ceb691a599afce48f5.squirrel@localhost>
Jun 16 18:56:34 attila-asus postfix/qmgr[7711]: C606F1D16: from=<attila@attila-farkas.homelinux.com>, size=719, nrcpt=1 (queue active)
Jun 16 18:56:34 attila-asus postfix/smtpd[8659]: disconnect from unknown[::1]
Jun 16 18:56:35 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:56:35 attila-asus postfix/smtp[8663]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 18:56:35 attila-asus postfix/smtp[8663]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 18:56:35 attila-asus postfix/smtp[8663]: C606F1D16: to=<mail@attila-farkas.sk>, relay=none, delay=0.51, delays=0.13/0.02/0.35/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 18:56:35 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=613/171
Jun 16 18:56:35 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:56:35 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=117/931
Jun 16 18:56:39 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:56:39 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=307/1419
Jun 16 18:58:03 attila-asus postfix/smtpd[8659]: connect from mail3.atlantis.sk[80.94.52.52]
Jun 16 18:58:03 attila-asus postfix/smtpd[8659]: setting up TLS connection from mail3.atlantis.sk[80.94.52.52]
Jun 16 18:58:04 attila-asus postfix/smtpd[8659]: Anonymous TLS connection established from mail3.atlantis.sk[80.94.52.52]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Jun 16 18:58:04 attila-asus postfix/smtpd[8659]: CC11A15D: client=mail3.atlantis.sk[80.94.52.52]
Jun 16 18:58:06 attila-asus postfix/cleanup[8662]: CC11A15D: message-id=<4C190297.40801@attila-farkas.sk>
Jun 16 18:58:06 attila-asus postfix/qmgr[7711]: CC11A15D: from=<mail@attila-farkas.sk>, size=1870, nrcpt=1 (queue active)
Jun 16 18:58:06 attila-asus postfix/local[8676]: warning: database /etc/aliases.db is older than source file /etc/aliases
Jun 16 18:58:06 attila-asus postfix/local[8676]: CC11A15D: to=<attila@attila-farkas.homelinux.com>, relay=local, delay=2.1, delays=2/0.02/0/0.06, dsn=2.0.0, status=sent (delivered to maildir)
Jun 16 18:58:06 attila-asus postfix/qmgr[7711]: CC11A15D: removed
Jun 16 18:58:06 attila-asus postfix/smtpd[8659]: disconnect from mail3.atlantis.sk[80.94.52.52]
Jun 16 18:58:20 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:58:20 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=85/361
Jun 16 18:58:23 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:58:23 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=292/1488
Jun 16 18:58:27 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:58:27 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=143/2679
Jun 16 18:59:21 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:59:21 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=143/2639
Jun 16 18:59:40 attila-asus postfix/smtpd[8659]: warning: ::1: address not listed for hostname localhost
Jun 16 18:59:40 attila-asus postfix/smtpd[8659]: connect from unknown[::1]
Jun 16 18:59:40 attila-asus postfix/smtpd[8659]: 37D971D2F: client=unknown[::1]
Jun 16 18:59:40 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:59:40 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=117/1668
Jun 16 18:59:40 attila-asus postfix/cleanup[8662]: 37D971D2F: message-id=<4bc8b37d14067cd6e5ae52136cc21950.squirrel@localhost>
Jun 16 18:59:40 attila-asus postfix/qmgr[7711]: 37D971D2F: from=<attila@attila-farkas.homelinux.com>, size=1069, nrcpt=1 (queue active)
Jun 16 18:59:40 attila-asus postfix/smtpd[8659]: disconnect from unknown[::1]
Jun 16 18:59:40 attila-asus postfix/smtp[8689]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 18:59:40 attila-asus postfix/smtp[8689]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 18:59:40 attila-asus postfix/smtp[8689]: 37D971D2F: to=<mail@attila-farkas.sk>, relay=none, delay=0.47, delays=0.32/0.02/0.14/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 18:59:40 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:59:40 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=1143/2181
Jun 16 18:59:41 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:59:41 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=292/1410
Jun 16 18:59:53 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 18:59:53 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=309/1874
Jun 16 19:00:11 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 19:00:11 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=292/1410
Jun 16 19:03:00 attila-asus postfix/anvil[8673]: statistics: max connection rate 1/60s for (smtp:80.94.52.52) at Jun 16 18:58:03
Jun 16 19:03:00 attila-asus postfix/anvil[8673]: statistics: max connection count 1 for (smtp:80.94.52.52) at Jun 16 18:58:03
Jun 16 19:03:00 attila-asus postfix/anvil[8673]: statistics: max cache size 1 at Jun 16 18:58:03
Jun 16 19:05:14 attila-asus postfix/qmgr[7711]: C606F1D16: from=<attila@attila-farkas.homelinux.com>, size=719, nrcpt=1 (queue active)
Jun 16 19:05:14 attila-asus postfix/qmgr[7711]: 37D971D2F: from=<attila@attila-farkas.homelinux.com>, size=1069, nrcpt=1 (queue active)
Jun 16 19:05:15 attila-asus postfix/smtp[9358]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 19:05:15 attila-asus postfix/smtp[9359]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 19:05:15 attila-asus postfix/smtp[9358]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 19:05:15 attila-asus postfix/smtp[9359]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 19:05:15 attila-asus postfix/smtp[9359]: 37D971D2F: to=<mail@attila-farkas.sk>, relay=none, delay=335, delays=335/0.13/0.2/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 19:05:15 attila-asus postfix/smtp[9358]: C606F1D16: to=<mail@attila-farkas.sk>, relay=none, delay=520, delays=520/0.4/0.21/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 19:15:14 attila-asus postfix/qmgr[7711]: C606F1D16: from=<attila@attila-farkas.homelinux.com>, size=719, nrcpt=1 (queue active)
Jun 16 19:15:14 attila-asus postfix/qmgr[7711]: 37D971D2F: from=<attila@attila-farkas.homelinux.com>, size=1069, nrcpt=1 (queue active)
Jun 16 19:15:45 attila-asus postfix/smtp[10014]: connect to mx0.atlantis.sk[92.240.247.6]:25: Connection timed out
Jun 16 19:15:45 attila-asus postfix/smtp[10013]: connect to mx0.atlantis.sk[92.240.247.6]:25: Connection timed out
Jun 16 19:16:15 attila-asus postfix/smtp[10014]: connect to mx2.atlantis.sk[85.248.69.127]:25: Connection timed out
Jun 16 19:16:15 attila-asus postfix/smtp[10013]: connect to mx2.atlantis.sk[85.248.69.127]:25: Connection timed out
Jun 16 19:16:15 attila-asus postfix/smtp[10014]: 37D971D2F: to=<mail@attila-farkas.sk>, relay=none, delay=995, delays=934/0.16/60/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: Connection timed out)
Jun 16 19:16:15 attila-asus postfix/smtp[10013]: C606F1D16: to=<mail@attila-farkas.sk>, relay=none, delay=1180, delays=1120/0.43/60/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: Connection timed out)
Jun 16 19:16:42 attila-asus postfix/master[7706]: terminating on signal 15
Jun 16 19:17:42 attila-asus postfix/master[2775]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 16 19:17:43 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 16 19:17:53 attila-asus postfix/master[2775]: reload configuration /etc/postfix
Jun 16 19:17:53 attila-asus postfix/qmgr[3538]: C606F1D16: from=<attila@attila-farkas.homelinux.com>, size=719, nrcpt=1 (queue active)
Jun 16 19:17:53 attila-asus postfix/qmgr[3538]: 37D971D2F: from=<attila@attila-farkas.homelinux.com>, size=1069, nrcpt=1 (queue active)
Jun 16 19:17:52 attila-asus postfix/smtp[3549]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 19:17:52 attila-asus postfix/smtp[3549]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 19:17:52 attila-asus postfix/smtp[3549]: 37D971D2F: to=<mail@attila-farkas.sk>, relay=none, delay=1093, delays=1093/0.21/0/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 19:18:13 attila-asus postfix/smtp[3547]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 19:18:13 attila-asus postfix/smtp[3547]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 19:18:13 attila-asus postfix/smtp[3547]: C606F1D16: to=<mail@attila-farkas.sk>, relay=none, delay=1299, delays=1279/0.24/20/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 19:37:33 attila-asus postfix/master[2775]: terminating on signal 15
Jun 16 19:38:39 attila-asus postfix/master[2776]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 16 19:38:40 attila-asus postfix/qmgr[2785]: 37D971D2F: from=<attila@attila-farkas.homelinux.com>, size=1069, nrcpt=1 (queue active)
Jun 16 19:38:40 attila-asus postfix/smtp[2799]: 37D971D2F: to=<mail@attila-farkas.sk>, relay=none, delay=2340, delays=2340/0.42/0.03/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=attila-farkas.sk type=MX: Host not found, try again)
Jun 16 19:38:41 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 16 19:38:51 attila-asus postfix/master[2776]: reload configuration /etc/postfix
Jun 16 19:38:51 attila-asus postfix/qmgr[3549]: C606F1D16: from=<attila@attila-farkas.homelinux.com>, size=719, nrcpt=1 (queue active)
Jun 16 19:38:51 attila-asus postfix/qmgr[3549]: 37D971D2F: from=<attila@attila-farkas.homelinux.com>, size=1069, nrcpt=1 (queue active)
Jun 16 19:38:52 attila-asus postfix/smtp[3556]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 19:38:52 attila-asus postfix/smtp[3552]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 19:38:52 attila-asus postfix/smtp[3556]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 19:38:52 attila-asus postfix/smtp[3552]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 19:38:52 attila-asus postfix/smtp[3552]: C606F1D16: to=<mail@attila-farkas.sk>, relay=none, delay=2537, delays=2537/0.16/0.24/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 19:38:52 attila-asus postfix/smtp[3556]: 37D971D2F: to=<mail@attila-farkas.sk>, relay=none, delay=2352, delays=2352/0.12/0.23/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 20:00:15 attila-asus postfix/master[2776]: terminating on signal 15
Jun 16 20:01:18 attila-asus postfix/master[2784]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 16 20:01:20 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 16 20:01:30 attila-asus postfix/master[2784]: reload configuration /etc/postfix
Jun 16 20:01:30 attila-asus postfix/qmgr[3550]: C606F1D16: from=<attila@attila-farkas.homelinux.com>, size=719, nrcpt=1 (queue active)
Jun 16 20:01:30 attila-asus postfix/qmgr[3550]: 37D971D2F: from=<attila@attila-farkas.homelinux.com>, size=1069, nrcpt=1 (queue active)
Jun 16 20:01:31 attila-asus postfix/smtp[3557]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 20:01:31 attila-asus postfix/smtp[3557]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 20:01:31 attila-asus postfix/smtp[3557]: C606F1D16: to=<mail@attila-farkas.sk>, relay=none, delay=3897, delays=3896/0.25/0.32/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 20:01:36 attila-asus postfix/smtp[3559]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 20:01:36 attila-asus postfix/smtp[3559]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 20:01:36 attila-asus postfix/smtp[3559]: 37D971D2F: to=<mail@attila-farkas.sk>, relay=none, delay=3716, delays=3711/0.21/5.2/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 20:11:50 attila-asus postfix/master[2784]: terminating on signal 15
Jun 16 20:12:59 attila-asus postfix/master[2801]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 16 20:13:00 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 16 20:13:10 attila-asus postfix/master[2801]: reload configuration /etc/postfix
Jun 16 20:13:10 attila-asus postfix/qmgr[3568]: C606F1D16: from=<attila@attila-farkas.homelinux.com>, size=719, nrcpt=1 (queue active)
Jun 16 20:13:10 attila-asus postfix/qmgr[3568]: 37D971D2F: from=<attila@attila-farkas.homelinux.com>, size=1069, nrcpt=1 (queue active)
Jun 16 20:13:11 attila-asus postfix/smtp[3577]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 20:13:11 attila-asus postfix/smtp[3579]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 20:13:11 attila-asus postfix/smtp[3577]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 20:13:11 attila-asus postfix/smtp[3579]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 20:13:11 attila-asus postfix/smtp[3577]: C606F1D16: to=<mail@attila-farkas.sk>, relay=none, delay=4597, delays=4596/0.3/0.24/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 20:13:11 attila-asus postfix/smtp[3579]: 37D971D2F: to=<mail@attila-farkas.sk>, relay=none, delay=4411, delays=4411/0.24/0.24/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 20:44:38 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 20:44:38 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=44/298
Jun 16 20:44:39 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 20:44:39 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=417/1317
Jun 16 20:44:39 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 20:44:39 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=292/1410
Jun 16 20:45:04 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 20:45:04 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=143/2649
Jun 16 20:45:31 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 20:45:31 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=143/2649
Jun 16 20:46:21 attila-asus postfix/smtpd[5123]: warning: database /etc/aliases.db is older than source file /etc/aliases
Jun 16 20:46:21 attila-asus postfix/smtpd[5123]: warning: ::1: address not listed for hostname localhost
Jun 16 20:46:21 attila-asus postfix/smtpd[5123]: connect from unknown[::1]
Jun 16 20:46:21 attila-asus postfix/smtpd[5123]: 8BCE71D56: client=unknown[::1]
Jun 16 20:46:21 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 20:46:21 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=117/1678
Jun 16 20:46:21 attila-asus postfix/cleanup[5126]: 8BCE71D56: message-id=<12a8a6d0224690065724d3ba558d26c0.squirrel@attila-farkas.homelinux.com>
Jun 16 20:46:21 attila-asus postfix/qmgr[3568]: 8BCE71D56: from=<attila@attila-farkas.homelinux.com>, size=1316, nrcpt=1 (queue active)
Jun 16 20:46:21 attila-asus postfix/smtpd[5123]: disconnect from unknown[::1]
Jun 16 20:46:22 attila-asus postfix/smtp[5128]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 20:46:22 attila-asus postfix/smtp[5128]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 20:46:22 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 20:46:22 attila-asus postfix/smtp[5128]: 8BCE71D56: to=<mail@attila-farkas.sk>, relay=none, delay=0.61, delays=0.38/0.01/0.22/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 20:46:22 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=1373/2181
Jun 16 20:46:22 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 20:46:22 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=292/1410
Jun 16 20:46:36 attila-asus dovecot: imap-login: Login: user=<attila>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Jun 16 20:46:36 attila-asus dovecot: IMAP(attila): Disconnected: Logged out bytes=309/2329
Jun 16 20:53:10 attila-asus postfix/qmgr[3568]: 8BCE71D56: from=<attila@attila-farkas.homelinux.com>, size=1316, nrcpt=1 (queue active)
Jun 16 20:53:10 attila-asus postfix/smtp[5382]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 20:53:10 attila-asus postfix/smtp[5382]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 20:53:10 attila-asus postfix/smtp[5382]: 8BCE71D56: to=<mail@attila-farkas.sk>, relay=none, delay=409, delays=409/0.02/0.2/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 20:59:48 attila-asus postfix/smtpd[5390]: warning: database /etc/aliases.db is older than source file /etc/aliases
Jun 16 20:59:49 attila-asus postfix/smtpd[5390]: connect from mail3.atlantis.sk[80.94.52.52]
Jun 16 20:59:50 attila-asus postfix/smtpd[5390]: setting up TLS connection from mail3.atlantis.sk[80.94.52.52]
Jun 16 20:59:50 attila-asus postfix/smtpd[5390]: Anonymous TLS connection established from mail3.atlantis.sk[80.94.52.52]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Jun 16 20:59:51 attila-asus postfix/smtpd[5390]: 5E4161D45: client=mail3.atlantis.sk[80.94.52.52]
Jun 16 20:59:51 attila-asus postfix/cleanup[5394]: 5E4161D45: message-id=<4C17EAAC.7070804@attila-farkas.sk>
Jun 16 20:59:51 attila-asus postfix/qmgr[3568]: 5E4161D45: from=<mail@attila-farkas.sk>, size=1863, nrcpt=1 (queue active)
Jun 16 20:59:51 attila-asus postfix/local[5395]: warning: database /etc/aliases.db is older than source file /etc/aliases
Jun 16 20:59:52 attila-asus postfix/local[5395]: 5E4161D45: to=<attila@attila-farkas.homelinux.com>, relay=local, delay=1.2, delays=1.1/0.01/0/0.04, dsn=2.0.0, status=sent (delivered to maildir)
Jun 16 20:59:52 attila-asus postfix/qmgr[3568]: 5E4161D45: removed
Jun 16 20:59:52 attila-asus postfix/smtpd[5390]: disconnect from mail3.atlantis.sk[80.94.52.52]
Jun 16 21:03:10 attila-asus postfix/qmgr[3568]: 8BCE71D56: from=<attila@attila-farkas.homelinux.com>, size=1316, nrcpt=1 (queue active)
Jun 16 21:03:10 attila-asus postfix/smtp[5761]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 21:03:10 attila-asus postfix/smtp[5761]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 21:03:10 attila-asus postfix/smtp[5761]: 8BCE71D56: to=<mail@attila-farkas.sk>, relay=none, delay=1009, delays=1008/0.02/0.35/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 21:03:12 attila-asus postfix/anvil[5392]: statistics: max connection rate 1/60s for (smtp:80.94.52.52) at Jun 16 20:59:49
Jun 16 21:03:12 attila-asus postfix/anvil[5392]: statistics: max connection count 1 for (smtp:80.94.52.52) at Jun 16 20:59:49
Jun 16 21:03:12 attila-asus postfix/anvil[5392]: statistics: max cache size 1 at Jun 16 20:59:49
Jun 16 21:23:10 attila-asus postfix/qmgr[3568]: 8BCE71D56: from=<attila@attila-farkas.homelinux.com>, size=1316, nrcpt=1 (queue active)
Jun 16 21:23:10 attila-asus postfix/qmgr[3568]: C606F1D16: from=<attila@attila-farkas.homelinux.com>, size=719, nrcpt=1 (queue active)
Jun 16 21:23:10 attila-asus postfix/qmgr[3568]: 37D971D2F: from=<attila@attila-farkas.homelinux.com>, size=1069, nrcpt=1 (queue active)
Jun 16 21:23:10 attila-asus postfix/smtp[6580]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 21:23:10 attila-asus postfix/smtp[6582]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 21:23:10 attila-asus postfix/smtp[6581]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 21:23:10 attila-asus postfix/smtp[6580]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 21:23:10 attila-asus postfix/smtp[6582]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 21:23:10 attila-asus postfix/smtp[6581]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 21:23:10 attila-asus postfix/smtp[6580]: 8BCE71D56: to=<mail@attila-farkas.sk>, relay=none, delay=2209, delays=2209/0.02/0.29/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 21:23:10 attila-asus postfix/smtp[6581]: C606F1D16: to=<mail@attila-farkas.sk>, relay=none, delay=8796, delays=8796/0.02/0.29/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 21:23:10 attila-asus postfix/smtp[6582]: 37D971D2F: to=<mail@attila-farkas.sk>, relay=none, delay=8611, delays=8610/0.03/0.28/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 22:03:10 attila-asus postfix/qmgr[3568]: 8BCE71D56: from=<attila@attila-farkas.homelinux.com>, size=1316, nrcpt=1 (queue active)
Jun 16 22:03:11 attila-asus postfix/smtp[7861]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 22:03:12 attila-asus postfix/smtp[7861]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 22:03:12 attila-asus postfix/smtp[7861]: 8BCE71D56: to=<mail@attila-farkas.sk>, relay=none, delay=4610, delays=4609/0.02/1.2/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 22:33:10 attila-asus postfix/qmgr[3568]: C606F1D16: from=<attila@attila-farkas.homelinux.com>, size=719, nrcpt=1 (queue active)
Jun 16 22:33:10 attila-asus postfix/qmgr[3568]: 37D971D2F: from=<attila@attila-farkas.homelinux.com>, size=1069, nrcpt=1 (queue active)
Jun 16 22:33:10 attila-asus postfix/smtp[8926]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 22:33:10 attila-asus postfix/smtp[8925]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 22:33:10 attila-asus postfix/smtp[8926]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 22:33:10 attila-asus postfix/smtp[8925]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 22:33:10 attila-asus postfix/smtp[8926]: 37D971D2F: to=<mail@attila-farkas.sk>, relay=none, delay=12810, delays=12810/0.02/0.23/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 22:33:10 attila-asus postfix/smtp[8925]: C606F1D16: to=<mail@attila-farkas.sk>, relay=none, delay=12996, delays=12995/0.02/0.24/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 23:13:10 attila-asus postfix/qmgr[3568]: 8BCE71D56: from=<attila@attila-farkas.homelinux.com>, size=1316, nrcpt=1 (queue active)
Jun 16 23:13:10 attila-asus postfix/smtp[10353]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 16 23:13:10 attila-asus postfix/smtp[10353]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 16 23:13:10 attila-asus postfix/smtp[10353]: 8BCE71D56: to=<mail@attila-farkas.sk>, relay=none, delay=8809, delays=8809/0.02/0.39/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 16 23:34:21 attila-asus postfix/master[2801]: terminating on signal 15
Jun 17 01:12:58 attila-asus postfix/master[2772]: daemon started -- version 2.5.5, configuration /etc/postfix
Jun 17 01:12:59 attila-asus postfix/qmgr[2781]: 8BCE71D56: from=<attila@attila-farkas.homelinux.com>, size=1316, nrcpt=1 (queue active)
Jun 17 01:12:59 attila-asus postfix/qmgr[2781]: C606F1D16: from=<attila@attila-farkas.homelinux.com>, size=719, nrcpt=1 (queue active)
Jun 17 01:12:59 attila-asus postfix/qmgr[2781]: 37D971D2F: from=<attila@attila-farkas.homelinux.com>, size=1069, nrcpt=1 (queue active)
Jun 17 01:13:00 attila-asus postfix/smtp[2795]: 8BCE71D56: to=<mail@attila-farkas.sk>, relay=none, delay=15998, delays=15998/0.71/0.02/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=attila-farkas.sk type=MX: Host not found, try again)
Jun 17 01:13:00 attila-asus postfix/smtp[2832]: C606F1D16: to=<mail@attila-farkas.sk>, relay=none, delay=22585, delays=22584/0.64/0.02/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=attila-farkas.sk type=MX: Host not found, try again)
Jun 17 01:13:00 attila-asus postfix/smtp[2833]: 37D971D2F: to=<mail@attila-farkas.sk>, relay=none, delay=22400, delays=22399/0.63/0.01/0, dsn=4.4.3, status=deferred (Host or domain name not found. Name service error for name=attila-farkas.sk type=MX: Host not found, try again)
Jun 17 01:13:00 attila-asus dovecot: dovecot v1.1.11 starting up (core dumps disabled)
Jun 17 01:13:11 attila-asus postfix/master[2772]: reload configuration /etc/postfix
Jun 17 01:13:11 attila-asus postfix/qmgr[3549]: 8BCE71D56: from=<attila@attila-farkas.homelinux.com>, size=1316, nrcpt=1 (queue active)
Jun 17 01:13:11 attila-asus postfix/qmgr[3549]: C606F1D16: from=<attila@attila-farkas.homelinux.com>, size=719, nrcpt=1 (queue active)
Jun 17 01:13:11 attila-asus postfix/qmgr[3549]: 37D971D2F: from=<attila@attila-farkas.homelinux.com>, size=1069, nrcpt=1 (queue active)
Jun 17 01:13:12 attila-asus postfix/smtp[3556]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 17 01:13:12 attila-asus postfix/smtp[3556]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 17 01:13:12 attila-asus postfix/smtp[3556]: C606F1D16: to=<mail@attila-farkas.sk>, relay=none, delay=22597, delays=22597/0.11/0.39/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 17 01:13:17 attila-asus postfix/smtp[3552]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 17 01:13:17 attila-asus postfix/smtp[3557]: connect to mx0.atlantis.sk[92.240.247.6]:25: No route to host
Jun 17 01:13:17 attila-asus postfix/smtp[3552]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 17 01:13:17 attila-asus postfix/smtp[3557]: connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host
Jun 17 01:13:17 attila-asus postfix/smtp[3552]: 8BCE71D56: to=<mail@attila-farkas.sk>, relay=none, delay=16016, delays=16010/0.11/5.2/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
Jun 17 01:13:17 attila-asus postfix/smtp[3557]: 37D971D2F: to=<mail@attila-farkas.sk>, relay=none, delay=22417, delays=22412/0.12/5.2/0, dsn=4.4.1, status=deferred (connect to mx2.atlantis.sk[85.248.69.127]:25: No route to host)
```

Is there anyone, please who knows what is the problem?

---

