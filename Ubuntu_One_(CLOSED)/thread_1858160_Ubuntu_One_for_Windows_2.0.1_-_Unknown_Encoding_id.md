---
title: "Ubuntu One for Windows 2.0.1 - Unknown Encoding idna"
date: 2011-10-11
forum: Ubuntu One (CLOSED)
---

### Post by Darth_Chaos7 on 2011-10-11
I installed the official Ubuntu One for Windows 2.0.1 client for my Windows XP system. However, when trying to set-up my pre-existing account for the first time, it doesn't work and I get this message in red letters at the bottom: "unknown encoding idna". It doesn't seem to be a typo problems in the credentials, so I don't know what could be the issue.

---

### Post by practic on 2012-01-07
I had the same problem after installing a UbuntuOne upgrade.

It seems that there were still some UbuntuOne components running in the background that were not terminated when the upgrade installed.

I opened up Task Manager, sorted by Image Name, and ended any processes that started with "ubuntuone". Then restarted Ubuntu One and all was fine.

Perhaps a restart of Windows would have resolved this also.

---

