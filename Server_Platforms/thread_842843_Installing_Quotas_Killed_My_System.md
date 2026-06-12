---
title: "Installing Quotas Killed My System"
date: 2008-06-27
forum: Server Platforms
---

### Post by artvarck on 2008-06-27
After installing quota my system is no longer usable:

I installed quotas using apt.  I then edited fstab so that / would be available for quotas (user and group).  Then I restarted.

The first clue that something was amiss was that the screen resolution was set to 640x480.  Once logged on I found that I had no networking capabilities.  The screen resolution using the GUI cannot be set to anything higher than 640.

I removed quotas from fstab, rebooted, but nothing has changed.  

What have I done here?  How do I troubleshoot the issue and what will fix it?

Thanks

---

### Post by bluefrog on 2008-06-29
you haven't done anything else than activating quotas before rebooting (which was useless by the way, mount -o remount / should have been enough)

Anyway it is very unlikely for quota to be your problem as activating quota is one thing (paste your fstab) but then you need to put some quota for them to be taken in account.

James Dupin

---

