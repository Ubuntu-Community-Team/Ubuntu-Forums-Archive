---
title: "Plenty of unused disk space but none available to use"
date: 2012-03-13
forum: Server Platforms
---

### Post by Rob Frost on 2012-03-13
Hi guys, Is there a Ubuntu guru out there who can explain why, within my root file system, Ubuntu is mis-reporting the available space and telling me root is full when it's not? You can assume I'm not a total numpty and that the space is correctly mounted within a filesystem etc.

The command df -h

shows /dev/md1 910G in size, mounted on / with 870G used. But it shows 100% Use and 0 Available. 870 out of 910 is NOT 100%!
Both Shift-deleting files (I've deleted 40G of files), and deleting then  locating all Trash folders and emptying them, successfully free up disk  space as reported everywhere, including by df, but fail to make any more space available to be used - it still says 100% use.

I do not have an excessive number of directories.

I have an additional 1.8TB mdadm volume mounted at /home/raid2 and my  suspicion is that the large filesystem is confusing Ubuntu re the available space, i.e.  Ubuntu is deducting the 1.8T disk usage from the 910G available  on / and concluding nothing is available. Perhaps the algorithm for detecting available space breaks down over 2TB?

I have no individual drive or array exceeding 2TB, though the sum of all mounted voumes is 2.7TB.

 Any ideas / suggestions to determine if that is in fact the case, and to diagnose and fix this issue?

Baobab is giving an error baobab:5165 error in dir /home/design:  Error stating file '/home/design/.gvfs': Permission denied.  Probably  not relevant, but thought I'd mention it.

Baobab correctly reports 2.7T total filesystem and 1.7T used at the top-line, but when you drill down into the folders it only shows 1T within the disk diagram & file system, and 100% used.

I plan to take one volume out of service at the next reboot.  It's conceivable that there may be a discrepancy between the volumes currently mounted, and the volumes set up to re-mount when the system re-boots. Could this be the source of the problem?

---

### Post by Cheesemill on 2012-03-13
Are you taking into account the 5% that the system reserves on all ext volumes?

[http://backdrift.org/freeing-disk-space-in-linux](http://backdrift.org/freeing-disk-space-in-linux)

---

### Post by Rob Frost on 2012-03-13
> **Cheesemill said:**
> Are you taking into account the 5% that the system reserves on all ext volumes?

[http://backdrift.org/freeing-disk-space-in-linux](http://backdrift.org/freeing-disk-space-in-linux)

Hmm i'll give that a look, maybe I'll free up more than 5%. Though it doesn't stand to reason, as it was letting me use the space fine until it filled up.  Then once it filled up and I deleted files it stays on 100% used.

---

### Post by Rob Frost on 2012-03-13
Sorry guys, my bad.  I deleted a further 15GB files and now it says space is available.  I just assumed if you delete & purge files it creates space!

---

