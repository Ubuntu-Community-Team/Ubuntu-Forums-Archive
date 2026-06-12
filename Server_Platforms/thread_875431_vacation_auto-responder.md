---
title: "vacation auto-responder"
date: 2008-07-30
forum: Server Platforms
---

### Post by StickyStyle on 2008-07-30
I was wondering what other admins out there use for vacation auto-responders for their users?  Currently I use the 'vacation' program in the repo, which works just fine except I have to setup the auto-responder and tear it down each time a user needs it.

Does anyone know of any other programs out there? preferably with a web interface.

---

### Post by pdwerryhouse on 2008-07-31
There is 'gnarwl', which uses accounts based in LDAP; no web interface, but it wouldn't be all that difficult to put one together for it.

---

### Post by lisati on 2008-07-31
It's up to you, but be careful: some people consider vacation responses to be spam: see [http://www.spamcop.net/fom-serve/cache/329.html](http://www.spamcop.net/fom-serve/cache/329.html) for more information.

---

### Post by StickyStyle on 2008-07-31
> **lisati said:**
> It's up to you, but be careful: some people consider vacation responses to be spam: see [http://www.spamcop.net/fom-serve/cache/329.html](http://www.spamcop.net/fom-serve/cache/329.html) for more information.

Yeah, it's important that you don't follow the directions of the vacation program and use a .forward.  I use vacation in a .procmailrc so that it only sends the auto-reply after the spam filtering has been blessed the email to the inbox, and it's quite rare that spam gets to the inbox at my company to begin with (not to toot my own horn :D ) - so forged from's and backscatter are not an issue so much.

---

