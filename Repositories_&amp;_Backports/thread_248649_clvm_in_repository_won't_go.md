---
title: "clvm in repository won't go"
date: 2006-09-01
forum: Repositories &amp; Backports
---

### Post by MishMich on 2006-09-01
I have checked out the threads on this, and nothing works for me - DD6

I tried the various apt-get install, remove, update, -f & dpkg commands - errors still there.

I am using lvm on my PC, unintentionally, but not sure how the cluster lvm package got there, as I have no use for it.  It is a real pain.  I flushed the cache-archive.  There is an entry under init.d for clvm.  When I do anything I get this sort of message:

Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  clvm
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 487kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 115492 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--remove):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

thanks

---

### Post by MishMich on 2006-09-01
went into /var/lib/dpkg/info & removed all the clvm.* scripts.

Next time I ran an apt-get command it gave me a one-line whinge about not finding the entries for clvm.  So, I went into synaptic, and it still showed clvm and a related package as installed.  I marked them for removal, and two other related packages were automatically marked, and this time they all went away properly.  Since then everything seems OK.  I can install packages OK now.  Not sure if this is a good way to get round the problem - maybe I'll find it has corrupted something later - but so far it seems OK.

Looking at the debian and aptitude sites, the next option would have been to go for a complete re-install.  As I'd done that once for the disappearing DNS entries already, I didn't really fancy that again.  So, if this works it will have saved me the bother.

Mish

---

