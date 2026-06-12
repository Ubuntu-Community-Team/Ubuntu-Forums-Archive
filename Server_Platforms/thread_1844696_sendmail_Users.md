---
title: "sendmail Users"
date: 2011-09-15
forum: Server Platforms
---

### Post by mbaker2311 on 2011-09-15
Is there a way to get a count of the number of sendmail users on my system?

---

### Post by zackwasa on 2011-09-15
it depends on how is sendmail set up on your server, if you have the default installation then any user from /etc/passwd with a valid shell account can send mail

---

### Post by cconstantine on 2011-09-16
You need to clarify what you mean by "sendmail users".

If you mean: how much (number of, size of, list of destination addresses, etc) email has each user on the system sent in some timeframe (e.g., yesterday)... Then you'll need to run analyze the log file from sendmail. That's normally handled by your syslog daemon, wherever it is configured to put the "mail" facility log messages.

---

