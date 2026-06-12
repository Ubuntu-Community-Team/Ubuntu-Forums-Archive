---
title: "Unable to login under another user other than main one after upgrade"
date: 2011-10-20
forum: Security
---

### Post by darylm74 on 2011-10-20
I have two accounts on my system, one is my main account (daryl) and the other is an oracle account (i.e. oracle) which is the owner of an installation of oracle 11g that I have.  I recently upgraded my system and now I can't login to oracle.  It flashes some stuff, at a command line level (I haven't been able to capture it) and then it goes back to the login screen.  I have no issues with my main account.

---

### Post by darylm74 on 2011-10-20
Nevermind, it is solved.  There was an odd line in the .profile and it was keeping me from logging in.  Odd that I never had issues before and wondering if it wasn't something to do with the upgrade

---

### Post by craigparker on 2011-10-24
I didn't see anything funky in .profile, and I have the same problem.  I compared .profile to another "good" user, and they're identical.

---

