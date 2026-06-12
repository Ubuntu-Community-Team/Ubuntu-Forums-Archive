---
title: "Calendar Server Import ICS File Failed"
date: 2013-12-14
forum: Server Platforms
---

### Post by huangyingw on 2013-12-14
Hi,
   I am following this  post [https://wiki.debian.org/HowTo/CalendarServer](https://wiki.debian.org/HowTo/CalendarServer), to setup my calendar server.
   Everything is ok, but seems that it does not ics file import.
   My intention is to export my google calendar out as a large ics file, and import it into my local calendar server.
   When importing, I got following error ```
Status Code: 2147500037, The request cannot be processed.

Server Replied with 403
```
   Could someone help me to solve this issue, 
   Or recommend a better calendar server for me, it is only for my personal usage, and my requirement is very simple: create, delete, import calendar.

---

### Post by Irihapeti on 2013-12-14
If you want to user CalendarServer, you'd probably get better help from the mailing list: [email]calendarserver-users@lists.macosforge.org[/email] (Also accessible at [http://blog.gmane.org/gmane.comp.macosx.calendarserver.user](http://blog.gmane.org/gmane.comp.macosx.calendarserver.user))

If it's just for yourself, you might find [Radicale]("http://radicale.org/") easier to setup.

I've used both, and I find Radicale a lot easier to manage.

---

### Post by huangyingw on 2013-12-15
hi Irihapeti,
    I am having trouble with radicale.
    Could you give me more document, the only docs I saw online are these two:
&#12288;&#12288;[http://www.iokom.com/drupal/post/setting-caldavcarddav-server-w-radicale-ubuntu](http://www.iokom.com/drupal/post/setting-caldavcarddav-server-w-radicale-ubuntu)
&#12288;&#12288;[http://radicale.org/user_documentation/](http://radicale.org/user_documentation/)

> **Irihapeti said:**
> If you want to user CalendarServer, you'd probably get better help from the mailing list: [email]calendarserver-users@lists.macosforge.org[/email] (Also accessible at [http://blog.gmane.org/gmane.comp.macosx.calendarserver.user](http://blog.gmane.org/gmane.comp.macosx.calendarserver.user))

If it's just for yourself, you might find [Radicale]("http://radicale.org/") easier to setup.

I've used both, and I find Radicale a lot easier to manage.

---

### Post by Irihapeti on 2013-12-15
Which version of Ubuntu are you running, and which version of Radicale are you trying to install?

It would also be useful to know what software you'll be using with it. E.g. Evolution, Thunderbird with Lightning, syncing to an Android phone.

---

