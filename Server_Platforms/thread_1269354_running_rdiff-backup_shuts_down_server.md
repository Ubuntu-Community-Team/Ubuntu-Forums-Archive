---
title: "running rdiff-backup shuts down server"
date: 2009-09-18
forum: Server Platforms
---

### Post by andrew_gatt on 2009-09-18
I've been using rdiff backup (specifically the rdiff-backup-usb.py script) to make incremental backups to a usb drive. This has been working nicely for a long time, but recently (last three nights) it has shutdown the server half way through. I know this because i've run it manually this morning and it shut it down.

I can't find any reference in any log files explaining why this is happening. I've checked syslog, kernel, debug, daemon and can't see anything unusual. None of the logs even note shutting down, so i'm presuming there is some kind of complete system crash happening?

I monitored the CPU temp while running the backup and its not near the trip points, so i don't think its that.

If anyone can help i'd really appreciate it. Is there a log file i can look at or a program i can use to trace back the problem?

Regards,

Andrew

---

### Post by openfly on 2009-09-18
What paths are you accessing for backups?  You'll want to avoid tapping anything in /dev/, /proc/ and other kernel interface points.

---

