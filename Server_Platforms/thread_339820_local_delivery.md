---
title: "local delivery"
date: 2007-01-16
forum: Server Platforms
---

### Post by marekdef on 2007-01-16
Hello,

I had set up ssmtp to forward mails to local area network mail server.
This works fine but ...
... when I have mail for my local users it is sent to this mail hub
(this includes cron jobs output and mail for root).

Then mail hub tries to deliver them to me VIA smtp on 25.
I do not have obviously nothing on 25th.

1. I do not get this mail
2. LAN administrator sees it and is annoyed by my mails aggregating on server.

I belive that I need a program that will deliver local mail to /var/mail/username
and non local mail to mailhub.

What is the best solution?
Everybody encourages me to install postfix, but I am not convinced as I would prefer simpler solution than fully featured SMTP server.

---

### Post by hal10000 on 2007-01-16
If i understand well what ssmtp does, then it can do nothing but delivering mail to a mailhub.
So I guess you either have to install someting like postfix on you local machine(s) or have the mail-server to be reconfigured to fit your needs.

---

### Post by Brazen on 2007-01-16
This may just not be possible on ssmtp.  As, apparently, others have said, Postfix can be configured to only send non-local mail to a smarthost and keep local mail on the server.

---

