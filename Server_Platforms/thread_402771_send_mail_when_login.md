---
title: "send mail when login"
date: 2007-04-06
forum: Server Platforms
---

### Post by meh on 2007-04-06
Hi!
anyone have an idé how to setup (in ubuntu server 6.10) so that when a user logs on (via ssh or "normal" login), ubuntu sends a mail telling what user/ip etc.

tnx

---

### Post by MrHorus on 2007-04-06
> **meh said:**
> Hi!
anyone have an idé how to setup (in ubuntu server 6.10) so that when a user logs on (via ssh or "normal" login), ubuntu sends a mail telling what user/ip etc.

tnx

Send a mail to who, the user or the system administrator?

You could set up a simple cron job that will analyse the logs for people logging in and this would probably suffice unless you wanted the email sent the minute the user logged in.

---

### Post by meh on 2007-04-06
to any given mail that I can specifi, eg. [email]mymail@mydomain.com[/email]
and yes, I would the mail to be sent the minute the users login.
I have no idea how to setup this system :S  but would be nice to have

---

