---
title: "Synchronizing on my own server"
date: 2017-10-28
forum: Ubuntu Cloud and Juju
---

### Post by pengyou2 on 2017-10-28
I would like to be able to sync firefox and mupy password vault to my own server and not to some cloud in the sky.  Are there any apps that will let me do this?

---

### Post by TheFu on 2017-10-28
Hundreds.  start with **rsync** - it has been around 20+ yrs and works extremely well.  You just need to tell  it the files and destinations. I wouldn't use the FF password system, if you care about security.

I use rsync to replicate my keepassx password DB to 6+ different systems every night.  I'm going 1-way, since my desktop is my "system of record."  Other systems are read-only, in my mind. keepassx uses a DB that is highly cross-plaform. I use the same DB on Windows, Android, and multiple different Linux systems. Binary compatibility is a wonderful thing.

Another option is to install **nextcloud** on your own server. It can be used like dropbox.  For a similar solution, there is **seafile** too. 

Lots of people by cloud-connected storage devices, but I find them, and their questionable security, scary.  Do we really want some 3rd party controlling access to storage on our internal networks? Really?  You and I say no, but most people don't really consider the issues.

---

