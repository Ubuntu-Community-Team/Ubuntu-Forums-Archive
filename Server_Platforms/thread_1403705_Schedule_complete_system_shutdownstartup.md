---
title: "Schedule complete system shutdown/startup?"
date: 2010-02-10
forum: Server Platforms
---

### Post by BrandonBan6 on 2010-02-10
Just curious if it is possible to schedule a complete system shutdown and start up? 

My box with ubuntu server on it is only used as an ssh/proxy server, so I would like save on energy costs and add a layer of security by completely shutting it down during the hours I do not use it.

---

### Post by tlsarles on 2010-02-10
Use Cron for the shutdown.
Some BIOS's have an option to turn on at a given time. Not very common tho

---

### Post by megamania on 2010-02-10
> **tlsarles said:**
> Use Cron for the shutdown.

And look into wake-on-lan for remote startup.

---

### Post by BrandonBan6 on 2010-02-10
thanks guys, i'll give this a try tonight!

---

### Post by repettus on 2010-03-13
I have tried cron with shutdown -h and shutdown -h +1 in an attempt to schedule an automatic shutdown in cron. If I enter shutdown -h in root cron, the computer shuts down if I hit launch task. However, it does not seem to be able to do it automatically in Ubuntu 9.10. Has anyone gotten it to work? I know there have been a lot of threads about this.

---

### Post by repettus on 2010-03-13
Sorry for being a newb. You have to type sudo shutdown in cron. It works now.

---

