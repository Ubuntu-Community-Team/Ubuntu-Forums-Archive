---
title: "[SOLVED] sendmail issue - DSN: Service unavailable"
date: 2007-11-26
forum: Server Platforms
---

### Post by alimadzi on 2007-11-26
I've been slowly getting sendmail up and running.  Seem to be making progress, but it's hard to say.  No more PHP errors at least, but the e-mails aren't being delivered.  Here's the latest mail.log output (e-mail address obfuscated):

```

Nov 26 11:10:15 idahostatesman sendmail[18276]: lAQIAFJ0018276: from=www-data, size=246, class=0, nrcpts=1, msgid=<200711261810.lAQIAFJ0018276@localhost.localdomain>, relay=www-data@localhost
Nov 26 11:10:15 idahostatesman sm-mta[18278]: lAQIAFEU018278: from=<www-data@localhost.localdomain>, size=494, class=0, nrcpts=1, msgid=<200711261810.lAQIAFJ0018276@localhost.localdomain>, proto=ESMTP, daemon=MSP-v4, relay=idahostatesman [127.0.0.1]
Nov 26 11:10:15 idahostatesman sendmail[18276]: lAQIAFJ0018276: to=<example@gmail.com>, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30246, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (lAQIAFEU018278 Message accepted for delivery)
Nov 26 11:10:15 idahostatesman sm-mta[18283]: STARTTLS=client, relay=idahostatesman.com.s8a1.psmtp.com., version=TLSv1/SSLv3, verify=FAIL, cipher=AES256-SHA, bits=256/256
Nov 26 11:10:16 idahostatesman sm-mta[18283]: lAQIAFEU018278: to=<example@gmail.com>, ctladdr=<www-data@localhost.localdomain> (33/33), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=120494, relay=idahostatesman.com.s8a1.psmtp.com. [64.18.7.10], dsn=5.0.0, stat=Service unavailable
Nov 26 11:10:16 idahostatesman sm-mta[18283]: lAQIAFEU018278: lAQIAGEU018283: DSN: Service unavailable
Nov 26 11:10:16 idahostatesman sm-mta[18283]: lAQIAGEU018283: to=<www-data@localhost.localdomain>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent

```

I'm really confused why it says "Service unavailable" followed by "Sent".  Not sure if this is a sendmail issue, a general server issue, or what.  I'd like to just get sendmail working and be done with it, but I'm open to alternatives such as exim if there's a compelling reason to switch.  Thanks in advance.

-Patrick

---

### Post by MJN on 2007-11-27
I would recommend Postfix - backwards compatible and practically a drop-in replacement for sendmail but far easier to configure. Sendmail's days are over...
 
Mathew

---

### Post by alimadzi on 2007-11-29
Sorry, forgot to subscribe to this thread.  Changed the default option for that so it won't happen again.

I eventually got sendmail working, so I'm just going to leave it for now.  I'm curious about the alternatives available, but just don't have time to fix something that isn't broken right now.  Thanks anyway for the suggestion.

---

### Post by MJN on 2007-11-29
Sure - understood. Just bear it in mind come your next 'tech refresh'!

Mathew

---

### Post by miltiad on 2008-01-16
How did you solve the problem ?

---

### Post by alimadzi on 2008-01-17
I fixed the problem by changing the hostname of my server.  Apparently "localhost.localdomain" will get rejected automatically by a lot of mail servers.  As soon as I changed my hostname to "extra.idahostatesman.com" (a domain that is hosted on the server), everything just worked and I had no more problems sending e-mail.

Hope this helps!

-Patrick

---

