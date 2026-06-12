---
title: "amtp auth failing after dovecot install"
date: 2008-11-01
forum: Server Platforms
---

### Post by BakeSale on 2008-11-01
A little background:

I've been administering an ubuntu lamp server for quite some time now and just using postfix no problem.  The other day a client requested webmail, so I installed dovecot (for imap) and squirrelmail, made sure it worked, and went to bed.

I woke up the next morning to my phone ringing off the hook.  pop3 didn't work.

I've tried uninstalling, reinstalling, and everything i can think of and now i'm to the point where:

-local delivery is working
-external mail will not come in (logs don't show any connections, not even failures)
-mail will only send through squirrelmail
-outlook or telnet into the server will NOT authenticate

If i had any hair, i'd be pulling it out now.  anyone out there have any insight?

thanks

---

