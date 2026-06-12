---
title: "User profiles"
date: 2009-07-17
forum: Server Platforms
---

### Post by asai on 2009-07-17
Is there a way to sentrally administer user profiles?
Say you want to have startmenu, desktop etc. the same for a lot of users.
Is this possible in any way? If so, how?

---

### Post by ajgreeny on 2009-07-17
Probably just copy over the hidden folder ~/.gconf from one user to the others.  There may be odd things that cause problems, but I'm not aware of any that are obvious.

---

### Post by scorp123 on 2009-07-17
> **asai said:**
> Is there a way to sentrally administer user profiles?
Say you want to have startmenu, desktop etc. the same for a lot of users. Why not configure it once and properly and then put all the relevant config files in **/etc/skel** ... so that any new user account would receive the same settings upon creation?

---

### Post by asai on 2009-07-17
Another goal here is to keep the users from altering the user profile. Therefore it had been very nice to have these profiles on a server, which upon login the user profile is loaded.
Is this possible?

---

