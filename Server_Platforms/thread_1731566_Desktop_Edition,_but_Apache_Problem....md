---
title: "Desktop Edition, but Apache Problem..."
date: 2011-04-17
forum: Server Platforms
---

### Post by El Muelio on 2011-04-17
Howdo,

I have just installed Ubuntu 11 on my Netbook, along with a LAMP stack, everything works fine up to there.

I have a seperate partition formatted to NTFS, so my documents are shared between Ubuntu and W7, amongst other things my Dropbox folder. I have got all my sites stored in my Dropbox, I thought I'd be clever and leave them in there, and simply create symlinks into /var/www for each site I need to run.

Problem is, when the symlinks are in place, I just get a 403 error, even when I boot opera as root.

Any pointers/help?

---

### Post by volkswagner on 2011-04-17
The files and symlinks need to be readable by www-data the user apache runs under.  Check the permissions of the files and links.

Dropbox handles symlinks well.  Why not leave the data in /var/www and symlink that folder to your dropbox so it gets synced?

---

