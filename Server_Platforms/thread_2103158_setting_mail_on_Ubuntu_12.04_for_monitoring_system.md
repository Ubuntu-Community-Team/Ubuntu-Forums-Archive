---
title: "setting mail on Ubuntu 12.04 for monitoring system"
date: 2013-01-09
forum: Server Platforms
---

### Post by tbaror on 2013-01-09
Hello ALL,

I am trying to set mail option on server that serve as monitoring server (check_mk)to be able to send mails.

I did install the mail component but its seems not able to send mails i get following message below 
My question where should i configure the parameters like mail from and allowed users.
Please advice
Thanks

```
Jan  9 12:37:34 it-srv-mn11 postfix/pickup[1911]: E9D8E1A2002E: uid=0 from=<root>
Jan  9 12:37:34 it-srv-mn11 postfix/cleanup[28401]: E9D8E1A2002E: message-id=<20130109103734.E9D8E1A2002E@it-srv-mn11>
Jan  9 12:37:35 it-srv-mn11 postfix/qmgr[1912]: E9D8E1A2002E: from=<root@dalet.com>, size=363, nrcpt=1 (queue active)
Jan  9 12:37:35 it-srv-mn11 postfix/local[28403]: E9D8E1A2002E: to=<tbaror@dalet.com>, relay=local, delay=0.28, delays=0.18/0/0/0.09, dsn=5.1.1, status=bounced (unknown user: "tbaror")
Jan  9 12:37:35 it-srv-mn11 postfix/cleanup[28401]: 220021A20045: message-id=<20130109103735.220021A20045@it-srv-mn11>
Jan  9 12:37:35 it-srv-mn11 postfix/bounce[28404]: E9D8E1A2002E: sender non-delivery notification: 220021A20045
Jan  9 12:37:35 it-srv-mn11 postfix/qmgr[1912]: 220021A20045: from=<>, size=2030, nrcpt=1 (queue active)
Jan  9 12:37:35 it-srv-mn11 postfix/qmgr[1912]: E9D8E1A2002E: removed
Jan  9 12:37:35 it-srv-mn11 postfix/local[28403]: 220021A20045: to=<root@dalet.com>, relay=local, delay=0.18, delays=0.1/0/0/0.08, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Jan  9 12:37:35 it-srv-mn11 postfix/qmgr[1912]: 220021A20045: removed

```

---

### Post by fernandoch on 2013-01-09
How did you set this up? Did you install mailutils also?

Take a look at this

[http://www.itbarna.com/enviar-correos-con-postfix-en-un-servidor-ubuntu](http://www.itbarna.com/enviar-correos-con-postfix-en-un-servidor-ubuntu)

Although it is in spanish. If you have problems, let me know.

---

### Post by chadk5utc on 2013-01-09
> **tbaror said:**
> Hello ALL,

I am trying to set mail option on server that serve as monitoring server (check_mk)to be able to send mails.

I did install the mail component but its seems not able to send mails i get following message below 
My question where should i configure the parameters like mail from and allowed users.
Please advice
Thanks

```
Jan  9 12:37:34 it-srv-mn11 postfix/pickup[1911]: E9D8E1A2002E: uid=0 from=<root>
Jan  9 12:37:34 it-srv-mn11 postfix/cleanup[28401]: E9D8E1A2002E: message-id=<20130109103734.E9D8E1A2002E@it-srv-mn11>
Jan  9 12:37:35 it-srv-mn11 postfix/qmgr[1912]: E9D8E1A2002E: from=<root@dalet.com>, size=363, nrcpt=1 (queue active)
Jan  9 12:37:35 it-srv-mn11 postfix/local[28403]: E9D8E1A2002E: to=<tbaror@dalet.com>, relay=local, delay=0.28, delays=0.18/0/0/0.09, dsn=5.1.1, status=bounced (unknown user: "tbaror")
Jan  9 12:37:35 it-srv-mn11 postfix/cleanup[28401]: 220021A20045: message-id=<20130109103735.220021A20045@it-srv-mn11>
Jan  9 12:37:35 it-srv-mn11 postfix/bounce[28404]: E9D8E1A2002E: sender non-delivery notification: 220021A20045
Jan  9 12:37:35 it-srv-mn11 postfix/qmgr[1912]: 220021A20045: from=<>, size=2030, nrcpt=1 (queue active)
Jan  9 12:37:35 it-srv-mn11 postfix/qmgr[1912]: E9D8E1A2002E: removed
Jan  9 12:37:35 it-srv-mn11 postfix/local[28403]: 220021A20045: to=<root@dalet.com>, relay=local, delay=0.18, delays=0.1/0/0/0.08, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Jan  9 12:37:35 it-srv-mn11 postfix/qmgr[1912]: 220021A20045: removed

```

I notice in the output of you message that there is from:root@dalet.com is this your domain? if not youll likely need to change and use a valid email as most mail servers require a valid account to send and receive for authentication.

---

