---
title: "bulkmail"
date: 2008-01-30
forum: Server Platforms
---

### Post by root_at_home on 2008-01-30
Hi there

I have a few clients that wants to send out bulkmails like newsletters to their clients....

Can someone help me to setup something that will make this easier than to mail each one at a time?

Thanks
Root_at_home

---

### Post by bukwirm on 2008-01-30
You can setup mailing lists - investigate [Mailman]("http://www.gnu.org/software/mailman/index.html").

---

### Post by HermanAB on 2008-01-30
Mailman together with Postfix will work.  Citadel can also do mailing lists, so it should not be a big deal.

---

### Post by root_at_home on 2008-02-03
Does anyone have a HOWTO to setup Mailman together with Postfix?

Regards
Root_at_home

---

### Post by bukwirm on 2008-02-03
The Mailman website has some documentation.

If I remember correctly, if you just install from the repositories and go though the main Mailman config file it works without any more effort.

By the way, you'll need Apache (or some other webserver, but Mailman works with Apache2), for the web-based list management interface.

---

### Post by radarhahaha on 2008-04-25
You can use the programs from [www.massmailsoftware.com](www.massmailsoftware.com) to send bulk mails to anyone.
from
radarhahaha at hotmail dot com

---

