---
title: "Foldershare (Windows Live Sync)-Like Software for Linux/Win/Mac"
date: 2009-10-29
forum: The Cafe
---

### Post by flipper9 on 2009-10-29
Just throwing this out there to see if there is interest...

Cloud computing is all the rage right now, and while it is a nice idea, there is always the problem of what to do when you are offline and with security and costs associated with storing your files on someone else's server.  

Foldershare (and subsequently bought out by Microsoft and renamed "Windows Live Sync") was a concept that got rid of the idea of storing your files on a server (and also paying for server space) and allowed you to easily synchronize files between different computers and on different operating systems.  Initially the idea was to support Windows, Macintosh, and Linux...but as you would expect, once bought out by Microsoft, the idea of supporting Linux was dropped.

Why is there no OSS version of this idea in existence?

Yes; I know there are utilities to synchronize files, but they are not intuitive...require lots of complicated setup...or are part of commercial packages that also sell server space...and have limited support for all the major operating systems.

Question: anyone currently working on or could we get a software package setup to do the following...

1. Replicate the ease of use of Foldershare (aka Windows Live Sync). 
2. All GUI setup (with option for command-line, cfg configuration)
3. Runs on all popular OS (Windows, Macintosh OsX, Linux, and possibly others)
4. Support syncing directories/folders easily between groups of people or just one person across multiple computers.
5. Be free of charge to use

---

### Post by dragos240 on 2009-10-29
Dropbox does this too. It's for win, mac, and linux.

---

### Post by dvlchd3 on 2009-10-29
[http://ubuntuforums.org/showthread.php?t=1080128](http://ubuntuforums.org/showthread.php?t=1080128)

---

### Post by flipper9 on 2009-10-29
Thanks for the info!  Unfortunately Dropbox has limits, and you have to pay to go past those.  I'm looking for something that is free, can be used by the users themselves without an intermediary that you have to pay a fee to.  Currently Foldershare requires a server to coordinate everything...maybe something can be developed that wouldn't require that, or would only lightly have to use a central server to get things connected?

---

### Post by flipper9 on 2009-10-29
Unfortunately, all the alternatives mentioned in that other thread are proprietary companies trying to sell storage on their servers.  I'm not looking to store data on a central server, but to use the clients to store data on each other's hard drives.  Foldershare (Windows Live Sync) provides such a capability but is proprietary, and doesn't work on Linux (or Wine for that matter).  Also I'm looking to not have any artificial limits placed on bandwidth or storage space, as those should be determined by what the clients support.

I'm looking for an OSS solution, or to start one.

P.S.  just to say that I'm basically looking to replicate what Foldershare does plus...
1. Remove the requirement for a centralized server, if possible
2. Support Linux (and other operating systems if possible)
3. Improve the network transport over what Foldershare provides (currently it doesn't intelligently break up files to share like many P2P programs do)

---

