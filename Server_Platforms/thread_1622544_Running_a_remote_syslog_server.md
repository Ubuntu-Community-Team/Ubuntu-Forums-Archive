---
title: "Running a remote syslog server"
date: 2010-11-15
forum: Server Platforms
---

### Post by Naatan on 2010-11-15
Hi, I've been trying to get a syslog server running for 2 hours now and just can't seem to progress.

I have a Mac dev machine configured to forward certain syslog entries to a remote syslog host. It's configured to forward them to my Ubuntu server. The Ubuntu server currently has rsyslog installed (tried syslog-ng as well).

I cannot for the life of me get it to log to a file. When I send an emergency level log message I will receive the message on the terminal of the Ubuntu server, but the message itself is not added to any file that I know of (at least not in the /var/logs directory).

I basically just use the default config files but with remote UDP enabled. I have not changed any paths what so ever. I suppose I need to add a config setting to have it log to a certain file for remote sessions? If that's the case I really wish someone would have documented it somewhere.

I would greatly appreciate any help I can get.

Thank you

---

