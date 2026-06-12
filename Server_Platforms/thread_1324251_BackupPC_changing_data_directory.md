---
title: "BackupPC: changing data directory"
date: 2009-11-12
forum: Server Platforms
---

### Post by memilanuk on 2009-11-12
Hello,

I've installed BackupPC and it looks as though I have things working... I started a full backup of a Vista PC, and after a few minutes remembered that the default directory for the 'backuppc' user is /var/lib/backuppc, which is under the / directory on my main hard drive (13GB) vs. under /srv/backuppc on my storage drive (500GB RAID 1 array).  I stopped the backup, and now I'm in a bit of a quandary.

It looks like from the documentation that if I change _TOPDIR_ in the config files to '/srv/backuppc' and move the applicable files to that location that everything should work okay.  Sorting out the permissions and such might take me a bit, but it looks like it *should* work.  The interesting part is that when I search back through the BackupPC-users list, there is some discussion on using symlinks to /var/lib/backuppc because apparently the data directory was hard-coded into the application back in past versions (circa 2006 or BackupPC v2.x).  It seems like that would cause some problems if one wanted to also backup the local computer - causing a loop of backing up to the location that you are backing up - unless some steps were taken to exclude certain directories.  Seems like just moving the data directory to the /srv storage drive in the config file wouuld be simpler/cleaner... and one of the other things that I found was that apparently at some point in the past, at least the Debian package for BackupPC asked where you wanted the data directory to be at, instead of now where it just automatically installs it as /var/lib/backuppc.  The install asks me which apache server I want to use, but not where I want to store the backups at - how much sense does that make?

At any rate, I was curious if anyone else had had any experiences to share regarding changing the data directory to somewhere besides the default - any gotchas to watch out for would be much appreciated!

TIA,

Monte

---

