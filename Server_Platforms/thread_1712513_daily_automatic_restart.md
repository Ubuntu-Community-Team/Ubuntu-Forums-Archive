---
title: "daily automatic restart"
date: 2011-03-22
forum: Server Platforms
---

### Post by moo9801 on 2011-03-22
is it possible ?

---

### Post by Cheesehead on 2011-03-22
The command is 'shutdown -r TIME' ('-r' means restart, you choose the time). See 'man shutdown'

You can trigger it from an 'at' job, or a 'cron' job, or stick it in a different daily task script (like after daily backups complete), or just by typing it everyday on the command line hours ahead of time.

---

### Post by HermanAB on 2011-03-23
Yes, you can as shown above, but why would you want to?  A Linux machine can run for many years without restarting (until the hardware fails).

---

