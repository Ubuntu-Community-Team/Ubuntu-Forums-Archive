---
title: "Mailman behaving badly...any guru's who can help a sysadmin?"
date: 2006-08-16
forum: Server Platforms
---

### Post by HedonismBot on 2006-08-16
Simple yet deeply annoying issue with mailman.

We use a p3 1.13Ghz box with 1GB of ram to serve several mailing lists, using mailman with emergency moderation turned on. this lets us test the messages (they're html newsletters) and then aprove them for broadcast. We have one list of 3000, one of 80 and one of 85345 members (!) and they work....But alas, an issue:

The messages take forever to show up in the moderation queue, and sometimes don't show up at all. Checks to see swap usage, memory usage, tailing the logs etc. all seem to show it working, but all the moderation queues come back with "No new pending moderator requests" everytime. Spam get's through sometimes (into the queue), but our messages don't! We're using a recently upgraded box (from BSD 5.4 to Dapper 6.06 server) and it worked fine after the upgrade, but now (with a recent extra 2000 members) it chokes like this...

Any thoughts, or have any of y'all seen this error before?

Help would be appreciated, even if it's to better resources than the awful mailman docs....

[-o<

---

