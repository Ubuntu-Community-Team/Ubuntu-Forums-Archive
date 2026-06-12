---
title: "Every other boot/reboot seems to be missing startup details on boot screens"
date: 2015-06-19
forum: Server Platforms
---

### Post by Marc-NJ on 2015-06-19
I just recently installed Ubuntu 14.04.2 LTS to a Dell XPS 8300 system.  However, I've noticed something unusual - it seems that every other time I reboot the system, the normal [OK] or [fail] that normally lists a ton of stuff prior to getting the login prompt only lists 4 or 5 items.  This doesn't seem to impact the system actually starting the rest of the services, etc., but when looking at the /var/log/boot.log during these reboots, it also has only 4 or 5 things listed.  Then, when I go to reboot again, it shows me the usual 40 or so items with [OK] or [fail], and they also appear in the /var/log/boot.log - any ideas why this is occurring?


I also notice on these reboots where I seem to be missing a lot of info, that the screen that quickly appears before I start seeing the list of services starting up has some different information on it - it goes by very quickly, but seems to list something about "plymouth upstart bridge" (or similar) a bunch - but not sure where to find the logs of the output from this initial boot screen - maybe someone can point me towards where that file would be and I can post it?

---

### Post by Marc-NJ on 2015-09-02
Anyone have any thoughts or advice on this, or how I can troubleshoot it, or even if it's anything to worry about?  Thanks!

---

