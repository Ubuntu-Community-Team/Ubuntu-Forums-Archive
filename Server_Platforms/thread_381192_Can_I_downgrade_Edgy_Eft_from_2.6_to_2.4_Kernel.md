---
title: "Can I downgrade Edgy Eft from 2.6 to 2.4 Kernel?"
date: 2007-03-10
forum: Server Platforms
---

### Post by PhragMunkee on 2007-03-10
Ever since upgrading my server from Breezy Badger to Edgy Eft, I have been having serious problems with one of my RAID cards.  The problems did not start appearing until the upgrade.  Is it possible to downgrade to the 2.4 kernel without significant downtime or would it be easier to try to back everything up and re-install Dapper Drake?  If it's possible to downgrade, how do I do it?

I have tried **[posting about the hardware problems](http://ubuntuforums.org/showthread.php?t=361361)** before, but haven't received any sort of answer.  I'm stumped and tired of having to come into work to reboot my server several times a week.

---

### Post by christhemonkey on 2007-03-10
For starters 2.4 kernel wasnt used in dapper.

2.4 kernel branch was started a long time ago, and is generally used in things for embedded devices and the like.

You are wanting to downgrade your kernel, which shouldnt take too long.  The actual time the server needs to be off is only the time of a restart.  But then again i dont think downgrading a kernel is an easy thing to do.

The best way would probably be to compile a kernel from kernel.org, and then, the best thing might be to compile a new one which may have your problem fixed. (also did you file a bug report about your problem?)

For kernel compilation see here:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

or here:
[http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

---

