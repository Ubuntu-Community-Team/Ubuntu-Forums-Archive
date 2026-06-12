---
title: "How Do I Set Up a Mail Server?"
date: 2011-08-15
forum: Server Platforms
---

### Post by Shake 'n' Bake on 2011-08-15
I've done quite a bit of searching, and I can't find anything that will tell me what I need to make a mail server.  What I do find is from several years ago and is no longer relevant.

I have a fairly standard LAMP installation with Ubuntu 11.04, Apache, MySQL, and the latest version of PHP 5.  What I need to know is what other software do I need, and how to put it all together; from what I have read, I am pretty sure that PHP has some built-in mail functionality, but it requires some set up.  I have tried this before (but without PHP or MySQL), only to get nowhere.  If it makes much of a difference, I want this mainly so I can send account confirmations for my wiki (it's MediaWiki, by the way).

Thanks for your help.

---

### Post by wormyblackburny on 2011-08-15
Sounds like you need to set up a SMTP server. You might try reading this: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by haqking on 2011-08-15
This covers pretty much everything

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

it is 8.04 but still valid

---

### Post by Shake 'n' Bake on 2011-08-15
Thanks for the replies.  I followed the first suggestion and I confirmed that it is working locally, but I can not get mail to send from my wiki.  For example, when I request a new password, the mail never reaches its destination.

---

### Post by hawk2010 on 2011-08-16
paste your tail -100 /var/log/mail.log after sending the test message

---

### Post by Shake 'n' Bake on 2011-08-16
Here are the results of tail -100 /var/log/mail.log.  Sorry for using the code tags, it said I have 25 images in this and the code tag was the only way out.:


```
Aug 16 13:09:02 Eccentricity postfix/qmgr[1575]: 0272D10152E: from=<root@pwarren.dyndns.org>, size=1754, nrcpt=1 (queue active)
Aug 16 13:09:02 Eccentricity postfix/local[2569]: 0272D10152E: to=<root@pwarren.dyndns.org>, orig_to=<root>, relay=local, delay=0.29, delays=0.19/0.02/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Aug 16 13:09:02 Eccentricity postfix/qmgr[1575]: 0272D10152E: removed
Aug 16 13:39:01 Eccentricity postfix/pickup[2384]: 42AFE10152E: uid=0 from=<root>
Aug 16 13:39:01 Eccentricity postfix/cleanup[2674]: 42AFE10152E: message-id=<20110816173901.42AFE10152E@pwarren.dyndns.org>
Aug 16 13:39:01 Eccentricity postfix/qmgr[1575]: 42AFE10152E: from=<root@pwarren.dyndns.org>, size=1754, nrcpt=1 (queue active)
Aug 16 13:39:01 Eccentricity postfix/local[2676]: 42AFE10152E: to=<root@pwarren.dyndns.org>, orig_to=<root>, relay=local, delay=0.29, delays=0.19/0.02/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Aug 16 13:39:01 Eccentricity postfix/qmgr[1575]: 42AFE10152E: removed
Aug 16 14:02:56 Eccentricity postfix/qmgr[1575]: 05859101556: from=<www-data@pwarren.dyndns.org>, size=1036, nrcpt=1 (queue active)
Aug 16 14:02:57 Eccentricity postfix/smtp[2730]: 05859101556: host mailin-03.mx.aol.com[64.12.90.33] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 14:02:57 Eccentricity postfix/smtp[2730]: 05859101556: host mailin-01.mx.aol.com[64.12.90.1] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 14:02:58 Eccentricity postfix/smtp[2730]: 05859101556: host mailin-02.mx.aol.com[64.12.90.65] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 14:02:58 Eccentricity postfix/smtp[2730]: 05859101556: host mailin-02.mx.aol.com[205.188.190.1] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 14:02:58 Eccentricity postfix/smtp[2730]: 05859101556: to=<patstr@aol.com>, relay=mailin-01.mx.aol.com[205.188.59.194]:25, delay=71126, delays=71123/0.03/2.4/0, dsn=4.0.0, status=deferred (host mailin-01.mx.aol.com[205.188.59.194] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6)
Aug 16 14:09:01 Eccentricity postfix/pickup[2696]: 7869D10152E: uid=0 from=<root>
Aug 16 14:09:01 Eccentricity postfix/cleanup[2764]: 7869D10152E: message-id=<20110816180901.7869D10152E@pwarren.dyndns.org>
Aug 16 14:09:01 Eccentricity postfix/qmgr[1575]: 7869D10152E: from=<root@pwarren.dyndns.org>, size=1754, nrcpt=1 (queue active)
Aug 16 14:09:01 Eccentricity postfix/local[2766]: 7869D10152E: to=<root@pwarren.dyndns.org>, orig_to=<root>, relay=local, delay=0.29, delays=0.19/0.02/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Aug 16 14:09:01 Eccentricity postfix/qmgr[1575]: 7869D10152E: removed
Aug 16 14:39:01 Eccentricity postfix/pickup[2696]: B73AF10152E: uid=0 from=<root>
Aug 16 14:39:01 Eccentricity postfix/cleanup[2848]: B73AF10152E: message-id=<20110816183901.B73AF10152E@pwarren.dyndns.org>
Aug 16 14:39:01 Eccentricity postfix/qmgr[1575]: B73AF10152E: from=<root@pwarren.dyndns.org>, size=1754, nrcpt=1 (queue active)
Aug 16 14:39:01 Eccentricity postfix/local[2850]: B73AF10152E: to=<root@pwarren.dyndns.org>, orig_to=<root>, relay=local, delay=0.27, delays=0.19/0.02/0/0.06, dsn=2.0.0, status=sent (delivered to maildir)
Aug 16 14:39:01 Eccentricity postfix/qmgr[1575]: B73AF10152E: removed
Aug 16 15:09:01 Eccentricity postfix/pickup[2696]: EE40A10152E: uid=0 from=<root>
Aug 16 15:09:01 Eccentricity postfix/cleanup[2922]: EE40A10152E: message-id=<20110816190901.EE40A10152E@pwarren.dyndns.org>
Aug 16 15:09:02 Eccentricity postfix/qmgr[1575]: EE40A10152E: from=<root@pwarren.dyndns.org>, size=1754, nrcpt=1 (queue active)
Aug 16 15:09:02 Eccentricity postfix/local[2924]: EE40A10152E: to=<root@pwarren.dyndns.org>, orig_to=<root>, relay=local, delay=0.29, delays=0.2/0.02/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Aug 16 15:09:02 Eccentricity postfix/qmgr[1575]: EE40A10152E: removed
Aug 16 15:12:57 Eccentricity postfix/qmgr[1575]: 05859101556: from=<www-data@pwarren.dyndns.org>, size=1036, nrcpt=1 (queue active)
Aug 16 15:12:57 Eccentricity postfix/smtp[2948]: 05859101556: host mailin-04.mx.aol.com[205.188.146.194] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 15:12:57 Eccentricity postfix/smtp[2948]: 05859101556: host mailin-03.mx.aol.com[205.188.59.193] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 15:12:58 Eccentricity postfix/smtp[2948]: 05859101556: host mailin-04.mx.aol.com[64.12.138.161] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 15:12:58 Eccentricity postfix/smtp[2948]: 05859101556: host mailin-03.mx.aol.com[64.12.90.97] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 15:12:58 Eccentricity postfix/smtp[2948]: 05859101556: to=<patstr@aol.com>, relay=mailin-04.mx.aol.com[205.188.103.2]:25, delay=75325, delays=75324/0.03/0.95/0, dsn=4.0.0, status=deferred (host mailin-04.mx.aol.com[205.188.103.2] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6)
Aug 16 15:39:01 Eccentricity postfix/pickup[2979]: 38E7F10152E: uid=0 from=<root>
Aug 16 15:39:01 Eccentricity postfix/cleanup[3015]: 38E7F10152E: message-id=<20110816193901.38E7F10152E@pwarren.dyndns.org>
Aug 16 15:39:01 Eccentricity postfix/qmgr[1575]: 38E7F10152E: from=<root@pwarren.dyndns.org>, size=1754, nrcpt=1 (queue active)
Aug 16 15:39:01 Eccentricity postfix/local[3017]: 38E7F10152E: to=<root@pwarren.dyndns.org>, orig_to=<root>, relay=local, delay=0.28, delays=0.19/0.02/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Aug 16 15:39:01 Eccentricity postfix/qmgr[1575]: 38E7F10152E: removed
Aug 16 16:09:01 Eccentricity postfix/pickup[2979]: 6EAC110152E: uid=0 from=<root>
Aug 16 16:09:01 Eccentricity postfix/cleanup[3094]: 6EAC110152E: message-id=<20110816200901.6EAC110152E@pwarren.dyndns.org>
Aug 16 16:09:01 Eccentricity postfix/qmgr[1575]: 6EAC110152E: from=<root@pwarren.dyndns.org>, size=1754, nrcpt=1 (queue active)
Aug 16 16:09:01 Eccentricity postfix/local[3096]: 6EAC110152E: to=<root@pwarren.dyndns.org>, orig_to=<root>, relay=local, delay=0.25, delays=0.18/0.02/0/0.05, dsn=2.0.0, status=sent (delivered to maildir)
Aug 16 16:09:01 Eccentricity postfix/qmgr[1575]: 6EAC110152E: removed
Aug 16 16:22:57 Eccentricity postfix/qmgr[1575]: 05859101556: from=<www-data@pwarren.dyndns.org>, size=1036, nrcpt=1 (queue active)
Aug 16 16:22:57 Eccentricity postfix/smtp[3134]: 05859101556: host mailin-01.mx.aol.com[205.188.159.42] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 16:22:57 Eccentricity postfix/smtp[3134]: 05859101556: host mailin-02.mx.aol.com[205.188.190.1] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 16:22:57 Eccentricity postfix/smtp[3134]: 05859101556: host mailin-04.mx.aol.com[64.12.90.66] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 16:22:57 Eccentricity postfix/smtp[3134]: 05859101556: host mailin-04.mx.aol.com[64.12.138.161] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 16:22:58 Eccentricity postfix/smtp[3134]: 05859101556: to=<patstr@aol.com>, relay=mailin-03.mx.aol.com[205.188.59.193]:25, delay=79525, delays=79524/0.03/0.91/0, dsn=4.0.0, status=deferred (host mailin-03.mx.aol.com[205.188.59.193] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6)
Aug 16 16:39:01 Eccentricity postfix/pickup[2979]: AD68410152E: uid=0 from=<root>
Aug 16 16:39:01 Eccentricity postfix/cleanup[3177]: AD68410152E: message-id=<20110816203901.AD68410152E@pwarren.dyndns.org>
Aug 16 16:39:01 Eccentricity postfix/qmgr[1575]: AD68410152E: from=<root@pwarren.dyndns.org>, size=1754, nrcpt=1 (queue active)
Aug 16 16:39:01 Eccentricity postfix/local[3179]: AD68410152E: to=<root@pwarren.dyndns.org>, orig_to=<root>, relay=local, delay=0.28, delays=0.19/0.02/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Aug 16 16:39:01 Eccentricity postfix/qmgr[1575]: AD68410152E: removed
Aug 16 17:09:01 Eccentricity postfix/pickup[3223]: E35C110152E: uid=0 from=<root>
Aug 16 17:09:01 Eccentricity postfix/cleanup[3254]: E35C110152E: message-id=<20110816210901.E35C110152E@pwarren.dyndns.org>
Aug 16 17:09:02 Eccentricity postfix/qmgr[1575]: E35C110152E: from=<root@pwarren.dyndns.org>, size=1754, nrcpt=1 (queue active)
Aug 16 17:09:02 Eccentricity postfix/local[3256]: E35C110152E: to=<root@pwarren.dyndns.org>, orig_to=<root>, relay=local, delay=0.28, delays=0.19/0.02/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Aug 16 17:09:02 Eccentricity postfix/qmgr[1575]: E35C110152E: removed
Aug 16 17:32:57 Eccentricity postfix/qmgr[1575]: 05859101556: from=<www-data@pwarren.dyndns.org>, size=1036, nrcpt=1 (queue active)
Aug 16 17:32:58 Eccentricity postfix/smtp[3312]: 05859101556: host mailin-01.mx.aol.com[64.12.90.98] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 17:32:58 Eccentricity postfix/smtp[3312]: 05859101556: host mailin-02.mx.aol.com[64.12.90.65] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 17:32:58 Eccentricity postfix/smtp[3312]: 05859101556: host mailin-02.mx.aol.com[64.12.139.193] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 17:32:58 Eccentricity postfix/smtp[3312]: 05859101556: host mailin-03.mx.aol.com[64.12.90.97] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 17:32:59 Eccentricity postfix/smtp[3312]: 05859101556: to=<patstr@aol.com>, relay=mailin-01.mx.aol.com[205.188.146.193]:25, delay=83726, delays=83725/0.03/1.1/0, dsn=4.0.0, status=deferred (host mailin-01.mx.aol.com[205.188.146.193] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6)
Aug 16 17:39:02 Eccentricity postfix/pickup[3223]: 2E36B10152E: uid=0 from=<root>
Aug 16 17:39:02 Eccentricity postfix/cleanup[3335]: 2E36B10152E: message-id=<20110816213902.2E36B10152E@pwarren.dyndns.org>
Aug 16 17:39:02 Eccentricity postfix/qmgr[1575]: 2E36B10152E: from=<root@pwarren.dyndns.org>, size=1754, nrcpt=1 (queue active)
Aug 16 17:39:02 Eccentricity postfix/local[3337]: 2E36B10152E: to=<root@pwarren.dyndns.org>, orig_to=<root>, relay=local, delay=0.28, delays=0.19/0.02/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Aug 16 17:39:02 Eccentricity postfix/qmgr[1575]: 2E36B10152E: removed
Aug 16 18:09:01 Eccentricity postfix/pickup[3223]: 6538610152E: uid=0 from=<root>
Aug 16 18:09:01 Eccentricity postfix/cleanup[3409]: 6538610152E: message-id=<20110816220901.6538610152E@pwarren.dyndns.org>
Aug 16 18:09:01 Eccentricity postfix/qmgr[1575]: 6538610152E: from=<root@pwarren.dyndns.org>, size=1754, nrcpt=1 (queue active)
Aug 16 18:09:01 Eccentricity postfix/local[3411]: 6538610152E: to=<root@pwarren.dyndns.org>, orig_to=<root>, relay=local, delay=0.31, delays=0.19/0.02/0/0.1, dsn=2.0.0, status=sent (delivered to maildir)
Aug 16 18:09:01 Eccentricity postfix/qmgr[1575]: 6538610152E: removed
Aug 16 18:39:01 Eccentricity postfix/pickup[3465]: A4CCD10152E: uid=0 from=<root>
Aug 16 18:39:01 Eccentricity postfix/cleanup[3487]: A4CCD10152E: message-id=<20110816223901.A4CCD10152E@pwarren.dyndns.org>
Aug 16 18:39:01 Eccentricity postfix/qmgr[1575]: A4CCD10152E: from=<root@pwarren.dyndns.org>, size=1754, nrcpt=1 (queue active)
Aug 16 18:39:01 Eccentricity postfix/local[3489]: A4CCD10152E: to=<root@pwarren.dyndns.org>, orig_to=<root>, relay=local, delay=0.29, delays=0.19/0.02/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Aug 16 18:39:01 Eccentricity postfix/qmgr[1575]: A4CCD10152E: removed
Aug 16 18:42:58 Eccentricity postfix/qmgr[1575]: 05859101556: from=<www-data@pwarren.dyndns.org>, size=1036, nrcpt=1 (queue active)
Aug 16 18:42:59 Eccentricity postfix/smtp[3500]: 05859101556: host mailin-02.mx.aol.com[64.12.139.193] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 18:42:59 Eccentricity postfix/smtp[3500]: 05859101556: host mailin-01.mx.aol.com[64.12.90.1] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 18:42:59 Eccentricity postfix/smtp[3500]: 05859101556: host mailin-03.mx.aol.com[205.188.190.2] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 18:42:59 Eccentricity postfix/smtp[3500]: 05859101556: host mailin-03.mx.aol.com[64.12.90.97] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6
Aug 16 18:43:00 Eccentricity postfix/smtp[3500]: 05859101556: to=<patstr@aol.com>, relay=mailin-04.mx.aol.com[205.188.146.194]:25, delay=87927, delays=87926/0.03/0.97/0, dsn=4.0.0, status=deferred (host mailin-04.mx.aol.com[205.188.146.194] refused to talk to me: 554- (RTR:DU)  [http://postmaster.info.aol.com/errors/554rtrdu.html](http://postmaster.info.aol.com/errors/554rtrdu.html) 554  Connecting IP: 72.226.22.6)
Aug 16 19:09:01 Eccentricity postfix/pickup[3465]: DB03E10152E: uid=0 from=<root>
Aug 16 19:09:01 Eccentricity postfix/cleanup[3557]: DB03E10152E: message-id=<20110816230901.DB03E10152E@pwarren.dyndns.org>
Aug 16 19:09:01 Eccentricity postfix/qmgr[1575]: DB03E10152E: from=<root@pwarren.dyndns.org>, size=1754, nrcpt=1 (queue active)
Aug 16 19:09:02 Eccentricity postfix/local[3559]: DB03E10152E: to=<root@pwarren.dyndns.org>, orig_to=<root>, relay=local, delay=0.29, delays=0.19/0.02/0/0.08, dsn=2.0.0, status=sent (delivered to maildir)
Aug 16 19:09:02 Eccentricity postfix/qmgr[1575]: DB03E10152E: removed
Aug 16 19:39:02 Eccentricity postfix/pickup[3465]: 219F3101530: uid=0 from=<root>
Aug 16 19:39:02 Eccentricity postfix/cleanup[3655]: 219F3101530: message-id=<20110816233902.219F3101530@pwarren.dyndns.org>
Aug 16 19:39:02 Eccentricity postfix/qmgr[1575]: 219F3101530: from=<root@pwarren.dyndns.org>, size=1754, nrcpt=1 (queue active)
Aug 16 19:39:02 Eccentricity postfix/local[3657]: 219F3101530: to=<root@pwarren.dyndns.org>, orig_to=<root>, relay=local, delay=0.28, delays=0.17/0.02/0/0.09, dsn=2.0.0, status=sent (delivered to maildir)
Aug 16 19:39:02 Eccentricity postfix/qmgr[1575]: 219F3101530: removed
Aug 16 19:44:40 Eccentricity postfix/smtpd[3917]: connect from Eccentricity[::1]
Aug 16 19:45:18 Eccentricity postfix/smtpd[3917]: disconnect from Eccentricity[::1]
```

---

### Post by hawk2010 on 2011-08-17
Your public IP is in a blacklist. First of all you have to perform a diagnostic on your server to check if  it is an open relay before informing the blacklists to remove your IP. Also make sure you have setup reverse DNS. Which means if the recipient mail server resolves your IP to a DNS it should resolve. Otherwise you have lower reputation. Follow the steps

1. Go [http://www.mxtoolbox.com/diagnostic.aspx](http://www.mxtoolbox.com/diagnostic.aspx)
put your IP or the DNS name
Check if all is green, else take action

2. Goto [http://www.mxtoolbox.com/blacklists.aspx](http://www.mxtoolbox.com/blacklists.aspx)
Type your IP or the mail server domain name
If you are blacklisted then you have to inform the relevant blacklists to white list.

3. From your logs its indicated that AOL is using spamhaus and your IP is blocked. so go here and open up a support request to take it down from the blacklist.
[http://postmaster.aol.com/SupportRequest.php](http://postmaster.aol.com/SupportRequest.php)

---

### Post by Shake 'n' Bake on 2011-08-17
Thanks for the solution.  I would not have expected that.  Unfortunately, when I go to the white list application, I get a forbidden error.  And now that I know how big a hassle this is, I'm not sure it's worth it.  I'll try again later today and probably for the rest of the week.

---

### Post by SeijiSensei on 2011-08-18
Your IP address resolves to this hostname:

cpe-72-226-22-6.nycap.res.rr.com

You're on a residential connection via RoadRunner.  AOL won't accept mail from these addresses because they're likely to be spamming.  My server wouldn't take your mail either.

I don't know how far you'll get trying to appeal to Spamhaus and other "blackhole lists" to get your IP whitelisted.  I think it's pretty unlikely.

Running mail servers on residential connections is always a dicey proposition.  Your provider may not permit servers of any kind on your connection, and you might be subject to inbound and outbound blocks on the SMTP port 25.

---

