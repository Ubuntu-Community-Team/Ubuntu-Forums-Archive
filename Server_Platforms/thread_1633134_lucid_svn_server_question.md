---
title: "lucid svn server question"
date: 2010-11-28
forum: Server Platforms
---

### Post by inphektion on 2010-11-28
Just want some feedback on a few questions.  Probably more opinion based but I'm on the fence.
We are moving our production svn server to a VM.  It is currently on a physical server ubuntu 8.04 with subversion from the hardy repos (1.4.something) and we use BDB for the svn back-end.
The new VM server we will use lucid and map to iscsi storage array for the svn partition.  

1. Thinking of going from BDB to FSFS.  so far in our test this saves our svn DB a lot of space and is faster in our checkouts.  I didn't love FSFS back with svn 1.4 but with 1.6 and a few more features (like sharding etc) it seems to be the way to go.  Opinions here?

2. Should I use the subversion from the lucid repo?  It seems there are some nice bug fixes in its main stable which is at 1.6.13 and lucid seems to be at 1.6.6?  I might want/need them quicker than the lucid repo updates and that is IF they do.  Thoughts?

3.  How do you guys backup svn?  currently we do svnadmin dump.  This takes 5 hours to finish on our repository.  I think it'll be much faster with 1.6 and FSFS but i noticed there is an svnadmin hotcopy.  
Should we maybe do the hotcopy daily and the dump weekly?
or should i try to utilize svnadmin sync in some fashion?

---

### Post by James78 on 2010-11-29
1. I agree. You should do this, and it's a very good idea. If you need to backup the repositories before changing them to a new format, you'll need to do a svnadmin dump (hotcopy isn't meant for changing filesystem types)

3. After you change your repo format and everything, you'll only need hotcopy, which WILL be faster than dumping, and dumping will probably already be faster in the new version. Bye bye 5 hour long dumps! Oh, and no, all you'll need is hotcopy, not both.

This explains dump vs hotcopy
[http://svn.haxx.se/users/archive-2005-05/0842.shtml](http://svn.haxx.se/users/archive-2005-05/0842.shtml)

---

### Post by inphektion on 2010-11-29
Great thanks.  I see you avoided question 2 ;)

since my current svnadmin dump takes so long is there way to do the dump, then load while users are still using the old repo and then do it again grabbing only the recent checkins so downtime is minimal?

In other words:
I do the 5 hour dump and it gets entire repo up to current revision which is 7997.  As i take the time to load that to the new repository users are still using the old one.  Now after 7 hours i take the old repo offline and I just want to dump most recent, say 8192 - 7997 and load that to the new repo making sure it keeps those revision numbers the same.
This way the repo is only "down" as I'm dumping and loading the 8192 - 7997 which should be a short period of time.

---

### Post by James78 on 2010-11-30
I'm not sure. But I do know that the hotcopy method does not need the repository to be down at all. So it may very well be that as hotcopy is copying, when it's done, it always has the latest version (vs taking it down, having 100 more revisions to copy afterward)

---

