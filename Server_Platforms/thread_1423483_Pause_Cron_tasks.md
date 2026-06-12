---
title: "Pause Cron tasks?"
date: 2010-03-06
forum: Server Platforms
---

### Post by balishaggy on 2010-03-06
Hi, I am running Ubuntu Hardy Heron for a web server and I have several cron tasks set up.  I would like to pause the chron tasks while I am working on the server for updates etc...  For example, one task sends an email then sets a flag in the database indicating that an email was sent.  When I am updating my server, I shut down the clients I use to send email so the emails are not sent, yet the database flag is set.

Is there a way to pause the cron tasks?

Thank you,
John

---

### Post by Bachstelze on 2010-03-06
Just comment them out in your crontab.

---

