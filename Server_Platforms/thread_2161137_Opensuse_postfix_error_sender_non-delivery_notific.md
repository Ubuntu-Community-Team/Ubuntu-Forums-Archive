---
title: "Opensuse :postfix error: sender non-delivery notification , Email bounced"
date: 2013-07-09
forum: Server Platforms
---

### Post by xlimonta on 2013-07-09
[COLOR=#000000][FONT=Verdana]Jul 9 10:48:22 loki postfix/qmgr[3635]: 952866272C: from=<123@ccron.cu>, size=506, nrcpt=1 (queue active)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Jul 9 10:48:22 loki roundcube: User [/FONT][/COLOR][EMAIL="123@ccron.cu"]123@ccron.cu[/EMAIL][COLOR=#000000][FONT=Verdana] [192.168.30.191]; Message for [/FONT][/COLOR][EMAIL="postmaster@ccron.cu"]postmaster@ccron.cu[/EMAIL][COLOR=#000000][FONT=Verdana]; 250: 2.0.0 Ok: queued as 952866272C[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Jul 9 10:48:22 loki postfix/smtp[17497]: 952866272C: to=<postmaster@ccron.cu>, relay=none, delay=0.33, delays=0.15/0.17/0.01/0, dsn=5.4.6, status=bounced (mail for ccron.cu loops back to myself)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Jul 9 10:48:22 loki postfix/cleanup[17490]: EDB1162739: message-id=<20130709144822.EDB1162739@loki.ccron.cu>[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Jul 9 10:48:23 loki postfix/qmgr[3635]: EDB1162739: from=<>, size=2259, nrcpt=1 (queue active)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Jul 9 10:48:23 loki postfix/bounce[17499]: 952866272C: sender non-delivery notification: EDB1162739[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Jul 9 10:48:23 loki postfix/qmgr[3635]: 952866272C: removed[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Jul 9 10:48:23 loki postfix/smtp[17497]: EDB1162739: to=<123@ccron.cu>, relay=none, delay=0.07, delays=0.03/0.02/0.02/0, dsn=5.4.6, status=bounced (mail for ccron.cu loops back to myself)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Jul 9 10:48:23 loki postfix/qmgr[3635]: EDB1162739: removed[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Jul 9 10:48:23 loki postfix/smtpd[17487]: disconnect from localhost[127.0.0.1][/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Please some body , help me about, this mail, work fine sending mail to outside, but e-mail form outdoor and internal, don't have delivery notification, please help me[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Sorry for my ugly English.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Tks a lot[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Here is a config files:



[/FONT][/COLOR]

---

