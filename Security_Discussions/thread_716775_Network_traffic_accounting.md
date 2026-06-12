---
title: "Network traffic accounting"
date: 2008-03-06
forum: Security Discussions
---

### Post by john.belcher on 2008-03-06
I need to do monitoring/accounting of all network activity.  At a minimum I need to store host/port, destination/port and a time stamp.  This info needs to be accessible for weeks or months.  I like NTop but it doesn’t store host info for extended periods of time.  TCPdump files get unruly very quickly.   I have access to a span port and PIX syslog.

Are there any suggestions?

What would be nice is if there was a program that would write TCPDump type info to a sql database.   I think I could handle writing the queries myself.

---

### Post by The Cog on 2008-03-06
Google for "netflow collector". There are lots of them. The makers of ntop produce a netflow probe that can monitor the traffic and send netflow info to a collector.

---

### Post by john.belcher on 2008-03-07
Thanks, Will look into it.

---

