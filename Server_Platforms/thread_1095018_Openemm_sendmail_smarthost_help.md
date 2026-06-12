---
title: "Openemm sendmail smarthost help"
date: 2009-03-13
forum: Server Platforms
---

### Post by Craigt on 2009-03-13
I am trying to set up the smarthost option of sendmail. So I can use our exhange server to relay emails for Openemm. I have followed the configurations guides that I have found on the internet.

But I am getting errors in my MAILLOG. Please see below.

Any help would be much appreciated, I can post the config of my sendmail.mc if needs be.

> Mar 13 10:59:13 SERVERNAME sendmail[7101]: starting daemon (8.14.2): SMTP+queueing@00:05:00
Mar 13 10:59:13 SERVERNAME sendmail[7104]: starting daemon (8.14.2): queueing@00:05:00
Mar 13 10:59:13 SERVERNAME sendmail[7105]: n2DAj1fe006727: bogus queue file, uid=114, gid=126, mode=100660
Mar 13 10:59:13 SERVERNAME sendmail[7101]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 13 10:59:13 SERVERNAME sendmail[7101]: daemon MTA: problem creating SMTP socket
Mar 13 10:59:14 SERVERNAME sendmail[7105]: n2DAj1fe006727: Losing ./qfn2DAj1fe006727: bogus file uid/gid in mqueue
Mar 13 10:59:14 SERVERNAME sendmail[7105]: n2D9j1bG006432: bogus queue file, uid=114, gid=126, mode=100660
Mar 13 10:59:14 SERVERNAME sendmail[7105]: n2D9j1bG006432: Losing ./qfn2D9j1bG006432: bogus file uid/gid in mqueue
Mar 13 10:59:14 SERVERNAME sendmail[7104]: unable to write pid to /home/openemm/var/run/sendmail-mqueue-client.pid: Permission denied
Mar 13 10:59:14 SERVERNAME sendmail[7107]: starting daemon (8.14.2): queueing@00:01:00
Mar 13 10:59:14 SERVERNAME sendmail[7107]: unable to write pid to /home/openemm/var/run/sendmail-openemm-admin.pid: Permission denied
Mar 13 10:59:14 SERVERNAME sendmail[7110]: starting daemon (8.14.2): queueing@00:01:00
Mar 13 10:59:14 SERVERNAME sendmail[7110]: unable to write pid to /home/openemm/var/run/sendmail-openemm-queue.pid: Permission denied
Mar 13 10:59:18 SERVERNAME sendmail[7101]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 13 10:59:18 SERVERNAME sendmail[7101]: daemon MTA: problem creating SMTP socket
Mar 13 10:59:23 SERVERNAME sendmail[7101]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 13 10:59:23 SERVERNAME sendmail[7101]: daemon MTA: problem creating SMTP socket
Mar 13 10:59:27 SERVERNAME sm-mta[7222]: starting daemon (8.14.2): SMTP+queueing@00:10:00
Mar 13 10:59:28 SERVERNAME sendmail[7101]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 13 10:59:28 SERVERNAME sendmail[7101]: daemon MTA: problem creating SMTP socket
Mar 13 10:59:33 SERVERNAME sendmail[7101]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 13 10:59:33 SERVERNAME sendmail[7101]: daemon MTA: problem creating SMTP socket
Mar 13 10:59:38 SERVERNAME sendmail[7101]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 13 10:59:38 SERVERNAME sendmail[7101]: daemon MTA: problem creating SMTP socket
Mar 13 10:59:43 SERVERNAME sendmail[7101]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 13 10:59:43 SERVERNAME  sendmail[7101]: daemon MTA: problem creating SMTP socket
Mar 13 10:59:48 SERVERNAME  sendmail[7101]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 13 10:59:48 SERVERNAME  sendmail[7101]: daemon MTA: problem creating SMTP socket
Mar 13 10:59:53 SERVERNAME  sendmail[7101]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 13 10:59:53 SERVERNAME  sendmail[7101]: daemon MTA: problem creating SMTP socket
Mar 13 10:59:58 SERVERNAME  sendmail[7101]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 13 10:59:58 SERVERNAME  sendmail[7101]: daemon MTA: problem creating SMTP socket
Mar 13 11:00:03 SERVERNAME  sendmail[7101]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 13 11:00:03 SERVERNAME  sendmail[7101]: daemon MTA: problem creating SMTP socket
Mar 13 11:00:03 SERVERNAME  sendmail[7101]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: server SMTP socket wedged: exiting
Mar 13 11:29:14 SERVERNAME  sendmail[7406]: 00001000000000003: to=<USER@example.co.uk>, delay=00:00:33, xdelay=00:00:01, mailer=relay, 
pri=0, relay='example.example.local', dsn=5.1.2, stat=Host unknown (Name server: 'example.example.local': host not found)

---

### Post by Craigt on 2009-03-17
I have broke down the log messages when they actually happen. So it is easier to understand what is happening and when.

When the server starts:

> Mar 17 11:05:26 SERVERNAME sm-mta[5439]: starting daemon (8.14.2): SMTP+queueing@00:10:00

When I start Openemm

> Mar 17 11:13:17 SERVERNAMEsendmail[6491]: starting daemon (8.14.2): SMTP+queueing@00:05:00
Mar 17 11:13:17 SERVERNAME sendmail[6494]: starting daemon (8.14.2): queueing@00:05:00
Mar 17 11:13:17 SERVERNAME sendmail[6491]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 17 11:13:17 SERVERNAME sendmail[6491]: daemon MTA: problem creating SMTP socket
Mar 17 11:13:17 SERVERNAME sendmail[6497]: starting daemon (8.14.2): queueing@00:01:00
Mar 17 11:13:17 SERVERNAME sendmail[6500]: starting daemon (8.14.2): queueing@00:01:00
Mar 17 11:13:22 SERVERNAME sendmail[6491]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 17 11:13:22 SERVERNAME sendmail[6491]: daemon MTA: problem creating SMTP socket
Mar 17 11:13:27 SERVERNAME sendmail[6491]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 17 11:13:27 SERVERNAME sendmail[6491]: daemon MTA: problem creating SMTP socket
Mar 17 11:13:32 SERVERNAME sendmail[6491]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 17 11:13:32 SERVERNAME sendmail[6491]: daemon MTA: problem creating SMTP socket
Mar 17 11:13:37 SERVERNAME sendmail[6491]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 17 11:13:37 SERVERNAME sendmail[6491]: daemon MTA: problem creating SMTP socket
Mar 17 11:13:42 SERVERNAME sendmail[6491]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 17 11:13:42 SERVERNAME sendmail[6491]: daemon MTA: problem creating SMTP socket
Mar 17 11:13:47 SERVERNAME sendmail[6491]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 17 11:13:47 SERVERNAME sendmail[6491]: daemon MTA: problem creating SMTP socket
Mar 17 11:13:52 SERVERNAME sendmail[6491]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 17 11:13:52 SERVERNAME sendmail[6491]: daemon MTA: problem creating SMTP socket
Mar 17 11:13:57 SERVERNAME sendmail[6491]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 17 11:13:57 SERVERNAME sendmail[6491]: daemon MTA: problem creating SMTP socket
Mar 17 11:14:02 SERVERNAME sendmail[6491]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 17 11:14:02 SERVERNAME sendmail[6491]: daemon MTA: problem creating SMTP socket
Mar 17 11:14:07 SERVERNAME sendmail[6491]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: cannot bind: Address already in use
Mar 17 11:14:07 SERVERNAME sendmail[6491]: daemon MTA: problem creating SMTP socket
Mar 17 11:14:07 SERVERNAME sendmail[6491]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA: server SMTP socket wedged: exiting

When I send an email campaign with openemm

> Mar 17 11:29:18 SERVERNAME sendmail[6800]: 00001100000000003: to=<EXAMPLE@EXAMPLE.co.uk>, delay=00:00:30, xdelay=00:00:01, mailer=relay, 
pri=0, relay='EXAMPLE.EXAMPLE.local', dsn=5.1.2, stat=Host unknown (Name server: 'EXAMPLE.EXAMPLE.local': host not found)
Mar 17 11:45:01 SEVERNAME sendmail[6954]: n2HBj1UK006954: from=EXAMPLE, size=318, class=0, nrcpts=1, msgid=<200903171145.n2HBj1UK006954@EXAMPLE.EXAMPLE.local>, 
relay=EXAMPLE@localhost
Mar 17 11:45:01 SERVERNAME sendmail[6954]: n2HBj1UK006954: to=EXAMPLE, ctladdr=EXAMPLE (1000/1000), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30318, 
relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]
Mar 17 11:48:17 SERVERNAME sendmail[6962]: n2HBj1UK006954: bogus queue file, uid=1000, gid=126, mode=100660
Mar 17 11:48:17 SERVERNAME sendmail[6962]: n2HBj1UK006954: Losing ./qfn2HBj1UK006954: bogus file uid/gid in mqueue
Mar 17 11:56:18 SERVERNAME sm-mta[6978]: n2HBoYaC006978: timeout waiting for input from localhost during server cmd read
Mar 17 11:56:18 SERVERNAME sm-mta[6978]: n2HBoYaC006978: localhost [127.0.0.1] did not issue MAIL/EXPN/VRFY/ETRN during connection to MTA


---

