---
title: "ERROR while configure sendmail on ubuntu server"
date: 2009-12-15
forum: Server Platforms
---

### Post by mady03sam on 2009-12-15
[SIZE=3]hi, i recently installed sendmail on ma ubuntu server and after configuring sendmail.mc i went back to check ma mail.log im getting this 
[/SIZE]
[SIZE=3]Dec 15 18:31:36 AEvonserver sm-mta[19628]: starting daemon (8.14.3): SMTP+queueing@00:10:00
Dec 15 18:31:36 AEvonserver sm-mta[19628]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA-v4: cannot bind: Address already in use
Dec 15 18:31:36 AEvonserver sm-mta[19628]: daemon MTA-v4: problem creating SMTP socket
Dec 15 18:31:41 AEvonserver sm-mta[19628]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA-v4: cannot bind: Address already in use
Dec 15 18:31:41 AEvonserver sm-mta[19628]: daemon MTA-v4: problem creating SMTP socket
Dec 15 18:31:46 AEvonserver sm-mta[19628]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA-v4: cannot bind: Address already in use
Dec 15 18:31:46 AEvonserver sm-mta[19628]: daemon MTA-v4: problem creating SMTP socket
Dec 15 18:31:51 AEvonserver sm-mta[19628]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA-v4: cannot bind: Address already in use
Dec 15 18:31:51 AEvonserver sm-mta[19628]: daemon MTA-v4: problem creating SMTP socket
Dec 15 18:31:56 AEvonserver sm-mta[19628]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA-v4: cannot bind: Address already in use
Dec 15 18:31:56 AEvonserver sm-mta[19628]: daemon MTA-v4: problem creating SMTP socket
Dec 15 18:32:01 AEvonserver sm-mta[19628]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA-v4: cannot bind: Address already in use
Dec 15 18:32:01 AEvonserver sm-mta[19628]: daemon MTA-v4: problem creating SMTP socket
Dec 15 18:32:06 AEvonserver sm-mta[19628]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA-v4: cannot bind: Address already in use
Dec 15 18:32:06 AEvonserver sm-mta[19628]: daemon MTA-v4: problem creating SMTP socket
Dec 15 18:32:11 AEvonserver sm-mta[19628]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA-v4: cannot bind: Address already in use
Dec 15 18:32:11 AEvonserver sm-mta[19628]: daemon MTA-v4: problem creating SMTP socket
Dec 15 18:32:16 AEvonserver sm-mta[19628]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA-v4: cannot bind: Address already in use
Dec 15 18:32:16 AEvonserver sm-mta[19628]: daemon MTA-v4: problem creating SMTP socket
Dec 15 18:32:21 AEvonserver sm-mta[19628]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA-v4: cannot bind: Address already in use
Dec 15 18:32:21 AEvonserver sm-mta[19628]: daemon MTA-v4: problem creating SMTP socket
Dec 15 18:32:26 AEvonserver sm-mta[19628]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA-v4: cannot bind: Address already in use
Dec 15 18:32:26 AEvonserver sm-mta[19628]: daemon MTA-v4: problem creating SMTP socket
Dec 15 18:32:26 AEvonserver sm-mta[19628]: NOQUEUE: SYSERR(root): opendaemonsocket: daemon MTA-v4: server SMTP socket wedged: exiting

..................what's d wrong wid SMTP socket n how can i fix dis problem[/SIZE]

---

### Post by cj13579 on 2009-12-15
are you trying to send mail via a server that requires authentication?

---

