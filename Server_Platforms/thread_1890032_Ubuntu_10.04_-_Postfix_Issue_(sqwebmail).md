---
title: "Ubuntu 10.04 - Postfix Issue (sqwebmail)"
date: 2011-12-02
forum: Server Platforms
---

### Post by michaelsage on 2011-12-02
Hi all,

I have found this forum more than useful on more than one occasion, I now have a problem that I don't seem to be able to find an answer for.

I have a very basic postfix set-up which is working very nicely, apart from one problem. 

I have a sqwebmail site which works fine as well, apart from when it comes to sending. I haven't managed to work out if it is a sqwebmail issue or a postfix issue. 

The problem seems to be that postfix isn't putting the correct suffix on the from address, probably easiest if I attach the log so you can see. 


Dec  2 20:59:57 pris sqwebmaild: LOGIN, user=joe, ip=[xx.xx.xx.xx]
Dec  2 21:00:34 pris postfix/pickup[32570]: 4715F15A2803F: uid=0 from=<joe@pris>
Dec  2 21:00:34 pris postfix/cleanup[32624]: 4715F15A2803F: message-id=<20111202210034.4715F15A2803F@pris.theangel.net>
Dec  2 21:00:34 pris postfix/qmgr[32549]: 4715F15A2803F: from=<joe@pris>, size=409, nrcpt=1 (queue active)
Dec  2 21:00:34 pris postfix/smtp[32625]: 4715F15A2803F: to=<xxx@theangel.net>, relay=mx1.mxsweep.com[89.167.219.1]:25, delay=0.45, delays=0.02/0.01/0.35/0.08, dsn=2.6.0, status=sent (250 2.6.0  <20111202210034.4715F15A2803F@pris.theangel.net> Queued mail for delivery)

As you can see it is trying to send from joe@pris, this is causing the email not to be delivered. 

Any ideas?! Please!

Tia

M

---

