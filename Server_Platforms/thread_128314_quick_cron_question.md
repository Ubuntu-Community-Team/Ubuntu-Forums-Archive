---
title: "quick cron question"
date: 2006-02-11
forum: Server Platforms
---

### Post by bailey_ca on 2006-02-11
I'm somewhere in the middle-of-the-road when it comes to Linux, ie, I kinda know how to muddle around and hack stuff together, but I don't really know *that* much about it. I've installed and "maintained" (I use the term loosely) various Slack/RH 5/MDK 6-10/SuSE etc. systems, and I think I generally have an idea of what's going on. Ubuntu, being based on Debian, throws me for a loop occasionally. Case-in-point: Should it be emailing me cron reports?

I've followed the guide at [Flurdy]("http://flurdy.com/docs/postfix/") to set up a replacement for my aging MDK 9/Qmail MX, but I'm not quite sure what it's doing... Am I losing my cron reports? They're not being delivered to any virtual root mailboxes nor to root locally. There's no bounces in any of my mail logs. Cron is showing up in syslog though.

I can send mail to root or root@localhost and it's delivered. Cron reports seem lost; to start, where *should* they be delivered to on Ubuntu?

---

### Post by Koybe on 2006-02-11
I think it creates an alias to the default user.
Check for it.

---

### Post by bailey_ca on 2006-02-15
It does, and it's properly set. Upon further mucking around, there seems to be a problem with the way my transports are set up... Troubleshooting continues. :)

---

