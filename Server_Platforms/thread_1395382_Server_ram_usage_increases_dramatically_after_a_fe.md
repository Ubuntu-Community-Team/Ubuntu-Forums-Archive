---
title: "Server ram usage increases dramatically after a few days of uptime"
date: 2010-01-31
forum: Server Platforms
---

### Post by blubaustin on 2010-01-31
I was wondering why after a couple of days of my ubuntu server running, that it goes from starting off at 94mb of ram usage all the way up to 498mb of ram usage? Any ideas?

---

### Post by Sporkman on 2010-01-31
Try saving a list of everything running after a reboot:

ps aux > list_of_processes_after_reboot

and comparing with the same list after a few days - maybe you'll see what the cause is.

---

### Post by t4thfavor on 2010-01-31
It's cache, google Linux memory usage, and read a few of the articles.

The basic theory is unused RAM is wasted RAM. It's going to try and stuff everything it can into the RAM so that when you want to use it, it's faster than banging the disk to get it.

---

