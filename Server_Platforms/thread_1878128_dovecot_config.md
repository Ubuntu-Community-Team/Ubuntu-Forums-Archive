---
title: "dovecot config"
date: 2011-11-09
forum: Server Platforms
---

### Post by petr.bena on 2011-11-09
Hi, I have installed dovecot on my server, and while I can send email fine, I can't receive them, even those send on local host, this made stuff which used to work (email from cron, nagios) stop working, I tried to search forums but there are too many results and most of them are not related to this, so I have no clue, I followed the guide, anyway it doesn't work. There is no error in logs, MTA is postfix

This is result of send of mail message from petanb to petanb on localhost, nothing happen:

Nov 9 10:18:38 server postfix/cleanup[16331]: A52FC43D6B: message-id=<20111109091838.A52FC43D6B@server>
Nov 9 10:18:38 server postfix/qmgr[16327]: A52FC43D6B: from=<>, size=2062, nrcpt=1 (queue active)
Nov 9 10:18:38 server postfix/bounce[16335]: 8567D43D6A: sender non-delivery notification: A52FC43D6B
Nov 9 10:18:38 server postfix/qmgr[16327]: 8567D43D6A: removed
Nov 9 10:18:38 server postfix/smtp[16333]: A52FC43D6B: to=<[EMAIL="petanb@server.tm-irc.org"][COLOR=#444444]petanb@server.tm-irc.org[/COLOR][/EMAIL]>, relay=none, delay=0.01, delays=0.01/0/0/0, dsn=5.4.6, status=bounced (mail for server.tm-irc.org loops back to myself)

---

