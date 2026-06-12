---
title: "Long running rsync gets aborted and computer becomes unresponsive"
date: 2013-11-15
forum: Ubuntu Studio
---

### Post by mahender.didwania on 2013-11-15
I've been trying to sync some data between two hard-disks using rsync.
I leave it running and a few hours later, the computer is not powered off/shutdown automatically but becomes unresponsive, the rsync hasn't finished and the hard-disk activity has stopped, the screen is blank. I know rsync doesn't finish because when I try to rsync the next time, it tries transferring files although the two hard-disks have had no modifications to their data.  Power settings are set to always stay on, never stop hard disks and not invoke the screensaver, using settings-manager.

I've absolutely no idea why the screen goes blank and why the computer becomes unresponsive (only a hard reset can start it again).

---

### Post by TheFu on 2013-11-15
Might I suggest that you capture the progress and stats to a log file so you can see where the issue is happening?

**rsync --stats --progress   source target | tee ~/log.rsync-run-1**
Something like that.

Plus you might try adding verbose levels with -vvv

---

