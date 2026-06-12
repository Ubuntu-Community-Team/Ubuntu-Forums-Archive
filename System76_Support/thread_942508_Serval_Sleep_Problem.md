---
title: "Serval Sleep Problem"
date: 2008-10-09
forum: System76 Support
---

### Post by thinman1189 on 2008-10-09
I put my serval performance to sleep yesterday and didn't have time to use it last night so when I got up this morning I opened it up. I heard a four tone noise and there's a bubble coming out of the battery indicator stating "Sleep Problem. Your computer failed to suspend. Check the help file for common problems." This is the third time that I've seen this. I only see it if it's asleep overnight. If it's asleep for about an hour or so, I don't get this message. Any ideas?

---

### Post by thomasaaron on 2008-10-09
If this only happens intermittently on overnight suspends, it might be pretty hard to figure out.

If you can reproduce it, it would be a good idea to look at /var/log/messages and /var/log/syslog to see if they give any indicators of what went wrong when resuming.

---

