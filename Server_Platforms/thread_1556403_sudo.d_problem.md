---
title: "sudo.d problem"
date: 2010-08-19
forum: Server Platforms
---

### Post by fred2028 on 2010-08-19
I accidentally chmod-ed everything in /etc to 777 and broke sudo. I booted into recovery mode and chmod-ed /etc/sudoers to 0440 and /etc/sudoers.d/ to 0440 also. But now when I try sudo it says
> sudo: can't open /etc/sudoers.d/README: Permission denied
If I change it to 777 it complains that it's not 0440. If I change it to 0440 I get the above error. How do I fix this?

---

### Post by Lars Noodén on 2010-08-23
Do you mean *sudoers.d* instead?

chown -R root:root /etc/sudoers.d
chmod u=rwx,g=rx,o=rx /etc/sudoers.d/
chmod u=r,g=r,o=  /etc/sudoers.d/*

The files should be read only for the user **root** and the group **root**, nothing more for anyone.  The directory must be r x for everyone and for the group **root**, but only the user **root** gets write permission to the directory.

---

### Post by SilentThunderStorm on 2011-10-15
WOOT!

Just necro-bumped to say thank you.

I had been getting irritated with having to chmod a million files while trying to fix an Apache issue, and used chmod -R 7777 /etc...

Obviously, unwise.

You just saved me from a lifetime of pain for that decision, though.

Thank you again.

---

### Post by drvik on 2011-12-31
> **Lars Noodén said:**
> Do you mean *sudoers.d* instead?

chown -R root:root /etc/sudoers.d
chmod u=rwx,g=rx,o=rx /etc/sudoers.d/
chmod u=r,g=r,o=  /etc/sudoers.d/*

The files should be read only for the user **root** and the group **root**, nothing more for anyone.  The directory must be r x for everyone and for the group **root**, but only the user **root** gets write permission to the directory.

Just wanted to say a big thank you Lars for helping me to fix this problem after an hour of trying to do so myself...!!:popcorn:

---

### Post by cptahab313 on 2012-07-13
Fantastique! May the gods of strength bless you and your rainbow inspired third army! Woo Woo!!

^^ Doesn't make much sense, but it doesn't have to, the point is that I am happy that this fix worked PERFECTLY!!

---

### Post by wildmanne39 on 2012-07-14
Old thread closed.

---

