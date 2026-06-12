---
title: "SAEximRunCond expansion failure"
date: 2010-04-01
forum: Server Platforms
---

### Post by theyranos on 2010-04-01
I'm trying to set up Spamassassin on my mail server such that it doesn't scan any messages appearing to originate from a Blackberry, because they're invariably flagged as false-positives.

Unfortunately, I'm currently getting this: ```
2010-04-01 07:38:12 1NxIiy-0003KB-6o SA: PANIC: SAEximRunCond expansion failure
on ${!match {$message_id}{blackberry}} (but message was accepted)
``` in my paniclog.

The offending line is in /etc/exim4/sa-exim.conf, and reads like this ```

SAEximRunCond: ${!match {$message_id}{blackberry}}

```

I've tried a number of variations on this line with no success. From what I read in the exim docs, I expected the above would work. However, since it's clearly not, I'm hoping someone can point me in the right direction.

---

