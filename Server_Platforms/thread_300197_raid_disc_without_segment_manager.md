---
title: "raid disc without segment manager?"
date: 2006-11-15
forum: Server Platforms
---

### Post by gaspedalo on 2006-11-15
Hi, I got a Raid10 (Software) on my Ubtuntu 6.10 Server. Yesterday mdadm reported one raid as degraded. Smartctl reproted disc sdb as failed. I deactivated and replaced it with a new one. EVMS (which I use to control the raid system) added it as a spare and mdadm started to synch it. Now, after it finished everything seems to be up and running.
But, as you see in the attached screenshot, the old disks had a dos segment manager involved. The new added SDB doesn't, just the localdiscmanager. Now I am a little bit concerned that there is something not the way it outta be.

---

