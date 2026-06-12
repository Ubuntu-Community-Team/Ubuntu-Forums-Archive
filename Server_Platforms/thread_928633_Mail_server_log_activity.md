---
title: "Mail server log activity"
date: 2008-09-24
forum: Server Platforms
---

### Post by volkswagner on 2008-09-24
I finally have my mail server working.  Postfix/IMAP/courier/mysql-auth/squirrelMail.  I am able to use SquirrelMail, and evolution to send/rec mail.  I am using my isp's smtp-server for outgoing mail due to dynamic ip limits/rejects.


I have not been able to pin down reason the following errors.

	From /var/log/auth.log

Sep 24 02:57:47 Web postfix/smtpd[23772]: sql_select option missing
Sep 24 02:57:47 Web postfix/smtpd[23772]: auxpropfunc error no mechanism available
Sep 24 02:57:47 Web postfix/smtpd[23772]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql

at the same hour I see the following

From /var/log/mail.log

Sep 24 02:57:47 Web postfix/smtpd[23772]: connect from 114-44-129-223.dynamic.hinet.net[114.44.129.223]
Sep 24 02:57:47 Web postfix/smtpd[23772]: lost connection after CONNECT from 114-44-129-223.dynamic.hinet.net[114.44.129.223]
Sep 24 02:57:47 Web postfix/smtpd[23772]: disconnect from 114-44-129-223.dynamic.hinet.net[114.44.129.223]
Sep 24 02:57:54 Web postfix/smtpd[23772]: connect from 114-44-129-223.dynamic.hinet.net[114.44.129.223]
Sep 24 02:59:01 Web postfix/smtpd[23772]: lost connection after EHLO from 114-44-129-223.dynamic.hinet.net[114.44.129.223]
Sep 24 02:59:01 Web postfix/smtpd[23772]: disconnect from 114-44-129-223.dynamic.hinet.net[114.44.129.223]
Sep 24 03:02:21 Web postfix/anvil[23774]: statistics: max connection rate 2/60s for (smtp:114.44.129.223) at Sep 24 02:57:54
Sep 24 03:02:21 Web postfix/anvil[23774]: statistics: max connection count 1 for (smtp:114.44.129.223) at Sep 24 02:57:47
Sep 24 03:02:21 Web postfix/anvil[23774]: statistics: max cache size 1 at Sep 24 02:57:47

I checked the ip address, it is located in AU.  Is this some sort of break-in attempt?
This is early in the morning here in NY.   The creatures sure do come out at night
Please advise.

---

### Post by vagena on 2008-09-24
some people ramble for 10 minutes at lunchtime, some people send presents... I think we know who gives better gifts... heehee [/size]I really love these [Lace Wig](http://www.royalmewigs.com) [naruto costume](http://www.cosprops.com/cosplay-costumes-naruto-cosplay-c-14_15.html)  [naruto cosplay](http://www.cosprops.com/cosplay-costumes-naruto-cosplay-c-14_15.html)  [human hair wigs](http://www.royalmewigs.com/lace-human-hair-wigs-c-10.html)  [Cosplay Wigs](http://www.cosprops.com/cosplay-wigs-c-5.html)

---

