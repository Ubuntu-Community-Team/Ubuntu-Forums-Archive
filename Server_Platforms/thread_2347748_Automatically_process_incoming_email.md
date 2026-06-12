---
title: "Automatically process incoming email"
date: 2016-12-28
forum: Server Platforms
---

### Post by geohei on 2016-12-28
Hi.

I'm a newbie in email setup and configuration with Ubuntu server. The basic email configuration, I'll manage ... but I have a project requiring special email processing. The project is basically a conversion system, which receives PDF files attached in an email, processes the PDF and resents the outcome (TXT file) immediately back to the FROM: address.

So ...
1. I need an email address which is (somehow) permanently monitored.
2. As soon as a new email arrives, I need to trigger the conversion tool.
3. After this one has finished its job, a new e-mail with the TXT file as attach should be sent to the FROM: address.

Basically, it should be something like an auto-reply, but with an intermediate processing in between.

I don't need a complete solution, but hints where to start would be good.

Many thanks,

---

### Post by TheFu on 2016-12-29
procmail [http://manpages.ubuntu.com/manpages/xenial/man1/procmail.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/procmail.1.html)
vacation [http://manpages.ubuntu.com/manpages/xenial/man1/vacation.sendmail.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/vacation.sendmail.1.html)
If email isn't coming into your system, then use **fetchmail** to get it from external pop3s and imaps systems.

---

