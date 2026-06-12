---
title: "postfix 'status=bounced' unable to send email to a domain"
date: 2010-09-08
forum: Server Platforms
---

### Post by squinter on 2010-09-08
Hi all,

After a reboot of my VPS, I keep getting the following error when sending email to my domain (hosted on Google Email). I can send to other email addresses but my own. So it seems like postfix thinks all mydomain.co.nz is to be sent internally?

Sep  9 09:25:05 mydomain postfix/pickup[20784]: 0316C3CC68: uid=1000 from=<sidb>
Sep  9 09:25:05 mydomain postfix/cleanup[20806]: 0316C3CC68: message-id=<20100908212505.0316C3CC68@mydomain.co.nz>
Sep  9 09:25:05 mydomain postfix/qmgr[20783]: 0316C3CC68: from=<sidb@mydomain.co.nz>, size=326, nrcpt=1 (queue active)
Sep  9 09:25:05 mydomain postfix/local[20808]: 0316C3CC68: to=<orders@mydomain.co.nz>, relay=local, delay=0.74, delays=0.5/0.01/0/0.23, dsn=5.1.1, status=bounced (unknown user: "orders")
Sep  9 09:25:05 mydomain postfix/cleanup[20806]: 7B9043CC6B: message-id=<20100908212505.7B9043CC6B@mydomain.co.nz>
Sep  9 09:25:05 mydomain postfix/qmgr[20783]: 7B9043CC6B: from=<>, size=1973, nrcpt=1 (queue active)
Sep  9 09:25:05 mydomain postfix/bounce[20810]: 0316C3CC68: sender non-delivery notification: 7B9043CC6B
Sep  9 09:25:05 mydomain postfix/qmgr[20783]: 0316C3CC68: removed
Sep  9 09:25:07 mydomain postfix/local[20808]: 7B9043CC6B: to=<sidb@mydomain.co.nz>, relay=local, delay=1.9, delays=0.09/0/0/1.8, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Sep  9 09:25:07 mydomain postfix/qmgr[20783]: 7B9043CC6B: removed


How do I tell postfix that mydomain.co.nz is to be sent to Google email server?

---

### Post by lisati on 2010-09-08
Thread moved to "Server Platforms".....


You might want to check out Postfix's "transport" settings. 
One example of using "transport" can be found here: [http://www.nooblet.org/blog/2007/postfix-transport-maps-diverting-mail-traffic/](http://www.nooblet.org/blog/2007/postfix-transport-maps-diverting-mail-traffic/)

---

### Post by squinter on 2010-09-08
Solved

Just don't set mydomain.co.nz as local and in postfix's main.cf removed mydomain.co.nz from destination

---

