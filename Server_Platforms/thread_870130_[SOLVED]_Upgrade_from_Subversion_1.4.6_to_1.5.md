---
title: "[SOLVED] Upgrade from Subversion 1.4.6 to 1.5"
date: 2008-07-25
forum: Server Platforms
---

### Post by zdunham on 2008-07-25
I'm running Apache 2 with Subversion 1.4.6, is there any way to just upgrade to 1.5 without reinstalling Subversion or should I just reinstall Subversion with the same command I used before:

sudo apt-get install Subversion libapache2-svn

or is it better to just run Subversion alone?

Thanks in advance.

---

### Post by seffyroff on 2008-07-29
Good question.  AFAIK Subversion 1.5 hasn't made it into the Hardy packages yet due to incompatibilities between SVN 1.5 and some libraries Ubuntu uses.

in theory apt-get upgrade subversion would do the trick, but until someone nice pushes 1.5 to the package database you're on your own I'm afraid.  I'm currently contemplating building from source :(

---

