---
title: "trouble installing revelation - md5sum mismatch"
date: 2005-11-03
forum: Repositories &amp; Backports
---

### Post by cid on 2005-11-03
I installed revelation (gnome password mgr) on my laptop the other day w/o problem but trying to install it on my desktop today (same version: 5.10) results in this unhappiness (md5sum mismatch):

=====================
Reformatting apt-get(8), please wait...
root@coruscant:~ # apt-get install revelation
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  revelation
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 316kB of archives.
After unpacking 1126kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe revelation 0.4.3-2 [316kB]
Fetched 316kB in 1s (187kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/r/revelation/revelation_0.4.3-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/r/revelation/revelation_0.4.3-2_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
=====================

Tried update, no love. The revelation version doesn't appear to have changed so it's presumably an issue with my desktop system's configuration. Suggestions?

---

### Post by nick4mony on 2005-11-03
The only thing I can suggest is to find where it downloaded the relevation package (usually somewhere under /var/cache/apt/archives/ ) on both systems.

Compare the file names (relevation_VERSION_i386.deb)

Also run md5sum on each file and compare.  This will start to give clues what's gone wrong.

---

### Post by cid on 2005-11-03
Thanks for the recommendation. The file I downloaded from the us ubuntu archive today, although the exact same name and version as the one that successfully installed on my laptop the other day, did have a different md5sum than the one on my laptop. And for the record, it was failing all day via automatic apt-get download due to md5sum mismatch before I manually DL'd it by browsing through the archive. So it wasn't just a transmission error in the one I manually grabbed.

I copied the good .deb file from my laptop to /var/cache/apt/archives and retried
$  apt-get install revelation
and it worked fine now.

Which leaves me with the question, what's up with the archive's copy of the file? The dates are the same. Has somebody h4xored their current copy or could there be a more innocent explanation. Is there a proper way to contact ubuntu.com to warn/ask them? Only likely mechanism I saw on the site was via bugzilla and that doesn't seem right.

---

### Post by nick4mony on 2005-11-16
[QUOTE=cid]Is there a proper way to contact ubuntu.com to warn/ask them? Only likely mechanism I saw on the site was via bugzilla and that doesn't seem right.[/QUOTE]

I think if you put it in Bugzilla it will get the attention it deserves.  But first do a 'wget' (with the --no-cache option) to download the file again, then an MD5 to make sure it's not fixed.

---

