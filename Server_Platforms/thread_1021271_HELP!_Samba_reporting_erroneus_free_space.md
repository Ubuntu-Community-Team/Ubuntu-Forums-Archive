---
title: "HELP! Samba reporting erroneus free space"
date: 2008-12-25
forum: Server Platforms
---

### Post by vladk2k on 2008-12-25
I have samba enabled on a folder which resides on a 66 GiB partition
The partition also has other folders, such as my home dir, the ftp folder etc.
Windows sees the share as: 10GiB free out of 65GiB, not taking into account files that are not actually on the share

So far so good, I actually have 10GiB free
The problem is this - on the same server I have now put a 80GB HDD which is mounted in the samba share as a dir named "80Gdrv".
So, I should see something different about this, except I don't. Windows still says "10GiB free out of 65 GiB". If I put files (smaller than 10GiB) in the 80Gdrv dir, all is well, I still have 10GiB free. But if I want to put files that are larger than 10GiB, I get an error (Not enough free space at destination).

Is there any other way, except creating a new share, to see those 80GiB separately?

And another question - could I make it somehow that when I add folders in a dir, they automatically get symlinked in another dir?

---

