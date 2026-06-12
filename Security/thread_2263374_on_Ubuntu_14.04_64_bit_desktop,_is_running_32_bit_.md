---
title: "on Ubuntu 14.04 64 bit desktop, is running 32 bit library a security issue?"
date: 2015-01-31
forum: Security
---

### Post by anoldguy on 2015-01-31
I am running Ubuntu 14.04 64 bit desktop and I want to run a 32 bit software.  I could install an older, 32 bit library, but is this a security problem?  Does the 32 bit library get security updates through Software Updater?  

Specifics:  Berkeley BOINC runs fine.  I want to add the Quake-Catcher Network project, but it seems to require some 32 bit library items.  Don't want to downgrade the whole desktop for one piece of software.  On their user forum someone suggested installing ia32-libs from Precise.  Is adding the old library a security risk?

---

### Post by deadflowr on 2015-01-31
32-bit is still supported.

If you install a 32-bit package from the repos, then it'll be supported for security updates.
(If you compile or install a 32-bit package outside the repos, then you are on your own;
But this holds true regardless of arch)

There are a very large number users who currently are still running 32-bit systems.
And they are currently supported just as much as someone running a 64-bit system.

---

### Post by anoldguy on 2015-01-31
Thanks very much.  

I tried to install ia32-libs, but it suggested lib32z1, lib32ncurses5, and lib32bz2-1.0.  I'm installing those.  It's a relief to know that they will be updated.

Mike

---

