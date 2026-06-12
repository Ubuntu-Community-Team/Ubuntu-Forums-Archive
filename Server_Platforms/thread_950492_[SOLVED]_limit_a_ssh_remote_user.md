---
title: "[SOLVED] limit a ssh remote user"
date: 2008-10-17
forum: Server Platforms
---

### Post by porchrat on 2008-10-17
OK firstly I am not running a server release, I am running a desktop release of Hardy, but since this is more of a server-orientated question I thought I would post it here.

Is there any way to limit the access that a remote ssh user has to directories on the server?

I've been testing and although the user isn't in sudoers, which at least limits his destructive capabilities I still don't want him running around like a hummingbird on amphetamines moving stuff around in other users directories.

I mean other than changing the permissions of the directories in question.  I was just wondering if there was some sort of central configuration file where I could set which directories his group had access to...or something similar

EDIT: You know what...in retrospect this seems like a stupid question to ask, What I really would like is for the remote users to not be able to read other users directories, but at the same time I don't want to be using "su" in order be able to browse other users directories i.e. just removing "read" permissions for everyone except "user" for everyones /home would be a little annoying...I hope that made sense to you because it sort of did to me.

---

### Post by cdenley on 2008-10-17
[http://ubuntuforums.org/showthread.php?t=451510](http://ubuntuforums.org/showthread.php?t=451510)

I've seen hyper_ch recommend MySecureShell a few times, but I never tried it.
[http://mysecureshell.sourceforge.net/](http://mysecureshell.sourceforge.net/)

---

### Post by porchrat on 2008-10-17
> **cdenley said:**
> [http://ubuntuforums.org/showthread.php?t=451510](http://ubuntuforums.org/showthread.php?t=451510)

I've seen hyper_ch recommend MySecureShell a few times, but I never tried it.
[http://mysecureshell.sourceforge.net/](http://mysecureshell.sourceforge.net/)

MySecureShell looks good, but that first link was extremely helpful and I'm pretty sure it is going to solve my problem.  Thank you very much!

I'm going to mark this thread as solved, play around a bit, and "unsolve" the thread if these 2 suggestions are not able to do what I need.

Thanks again

---

