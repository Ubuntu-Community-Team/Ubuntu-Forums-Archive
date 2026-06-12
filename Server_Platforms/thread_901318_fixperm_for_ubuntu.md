---
title: "fixperm for ubuntu?"
date: 2008-08-26
forum: Server Platforms
---

### Post by jglepage on 2008-08-26
Hello all,

I goofed and did a recursive chown on some very important directories.  Like /etc.  It didn't screw up everything but it messed up enough.  I guess the moral of this story is to never do important sysadmin stuff at 0300, and if you do then type carefully.  And triple-check your scripts.

Does anyone know how to fix this?  In RPM-based systems there is a utility called fixperm that uses the info in the RPM's to reset ownership and permissions.  Does such a thing exist for Ubuntu?  Maybe some arcane feature of dpkg*?

---

