---
title: "Error running checksetup.pl"
date: 2008-02-08
forum: Server Platforms
---

### Post by call911 on 2008-02-08
I am a new user of Linux, Apache, MySQL, and Bugzilla.  I am trying to get Bugzilla running properly and have been making consistant progress until now.  I know I have something set or installed improperly between MySQL, Apache2 and Bugzilla.  I have been trying to stick to the manual thinking I had missed something somewhere.

I can't figure out what it is.  So here is the question:

How do I fix this error?
[B]Could not execute `/etc/bugzilla/localconfig'! ; make sure permissions are ok. at /usr/share/perl5/Bugzilla/Config.pm line 161.
Compilation failed in require at checksetup.pl line 505.
BEGIN failed--compilation aborted at checksetup.pl line 505.[/B]

Any help would be appreciated.

---

### Post by call911 on 2008-02-12
Bump.

---

### Post by ikonia on 2008-02-12
1.) check that the user you are tyring to install as has permissions on not just the script you are running, but all the subsiquent scripts your main one will want.

2.) The error is giving you some pointers where to look, 
At a guess without more details 
> 
Compilation failed in require at checksetup.pl line 505.

means that something in this script at line 505 is being executed that causes
> 
 /usr/share/perl5/Bugzilla/Config.pm line 161

to fail at line 161

---

