---
title: "Hardy Heron sending mail as &quot;unknown sender&quot;"
date: 2009-04-12
forum: Server Platforms
---

### Post by dratman on 2009-04-12
I am running 8.04.1 (Hardy Heron) on a dedicated server (as preinstalled by my server host), so of course I can be root. Everything is going really well. This one is a minor but puzzling problem: all my outgoing mail (from the Hardy server to anyone else out in the world) arrives as "unknown sender". More specifically, all mail sent by my server shows up with a blank "From" line.

So far this affects all outbound mail, I mean, mail originating on the server, such as messages sent by users with the mail (or mailx, etc.) command, and also from cron job output.

The server is running Postfix. What am I doing wrong?

Thank you.

Regards,

Ralph

---

### Post by hyper_ch on 2009-04-12
you got a hostname set?

---

### Post by dratman on 2009-04-13
Thank you for your reply.

Yes, I have a nice, simple, alphanumeric hostname set.

Note: If I run the "mail" command and add a "From:" header, then the resulting outbound message is normal -- that is, it carries the specified sender address, and it does not get marked "unknown sender."

But email from cron should automatically have a sender name, shouldn't it?

Ralph

---

### Post by hyper_ch on 2009-04-13
it has on my server a sender name... I think...

---

