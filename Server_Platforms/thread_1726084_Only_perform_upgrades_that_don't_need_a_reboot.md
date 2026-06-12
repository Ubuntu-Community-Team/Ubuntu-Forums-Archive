---
title: "Only perform upgrades that don't need a reboot?"
date: 2011-04-10
forum: Server Platforms
---

### Post by Jondice on 2011-04-10
Hello,

I like to leave my server up for long periods of time (everyone has their reasons for this I suppose).  

Is there a way to upgrade a system with all packages except those that require a reboot?  I do have Ksplice installed, but I've noticed that some packages (e.g. kernel upgrades but not only this) seem to still require a reboot.

Does aptitude safe-upgrade do this?  I'm guessing not.

---

### Post by BkkBonanza on 2011-04-11
In my experience on server builds when an upgrade needs a reboot, such as kernel versions, they are usually held back automatically. I guess that may not always be the case but it won't force a reboot without your confirming. It simply lets you know that one should be done. Ideally you would then schedule a reboot for a time that would least impact activity.

---

