---
title: "Performing Full  Backup of the Entire Server Via SSH"
date: 2005-11-28
forum: Server Platforms
---

### Post by sianz99 on 2005-11-28
How do I perform a full server backup remote with only a SSH connection. I have done some reading up and dump could be an option but any has tried it? Is there any other proven suggestions?

---

### Post by Hezekiah on 2005-11-28
While I'm in the process of deciding on something of that sort now, I've heard/read a fair amount of positive stuff concerning rdiff-backup.  It can tunnel over SSH, and keeps track of changes over time.  [http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/) is the homepage I believe.

I think this can be used to do a full backup, though as I said, I'm still in the process of studying this myself.

---

### Post by sianz99 on 2005-12-01
[QUOTE=Hezekiah]While I'm in the process of deciding on something of that sort now, I've heard/read a fair amount of positive stuff concerning rdiff-backup.  It can tunnel over SSH, and keeps track of changes over time.  [http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/) is the homepage I believe.

I think this can be used to do a full backup, though as I said, I'm still in the process of studying this myself.[/QUOTE]

Thanks Hezekiah, I will check this out. However, initially reading seemed to imply its more of changes tracking rather than a full OS backup.

---

### Post by J.C. Denton on 2005-12-01
[QUOTE=sianz99]How do I perform a full server backup remote with only a SSH connection. I have done some reading up and dump could be an option but any has tried it? Is there any other proven suggestions?[/QUOTE]
I'd utilize [rsync](http://samba.anu.edu.au/rsync/) over an [SSH](http://www.openssh.org) tunnel.  There's a good walkthrough over at [Mac OS X Hints](http://www.macosxhints.com).  It mostly applies to an Ubuntu/Linux system.  You'll want to ignore the part about the resource forks.  Every week or so, you could take a copy of the dump and mark it as a "full" backup.

[LIST]
[*][rsync backup walkthrough](http://www.macosxhints.com/article.php?story=20031024013757927)
[/LIST]

Hope this helps :)!

---

