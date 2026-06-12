---
title: "messed up my java...PLZ HELP!!!"
date: 2007-06-24
forum: Repositories &amp; Backports
---

### Post by Ahslan on 2007-06-24
when i was installing java, a screen came up for me to accept java's agreement, but i wasnt able to continue...i tried pressing enter and clicking the "ok" but nothing worked...so i closed the window...now when i try install it again, i get an error saying :
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

and from the terminal i get:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

Now i have no idea what to do? Can anyone PLZ HELP!!!

---

### Post by moredhel on 2007-06-24
you should of pressed tab then spacebar to accept it.

simply type

dpkg --configure -a

into terminal, then try again.

---

### Post by Ahslan on 2007-06-24
when i do that it says:
dpkg: requested operation requires superuser privilege

??? i am the only computer user...what do i do?

---

### Post by YoG%*@ on 2007-06-24
> **Ahslan said:**
> when i do that it says:
dpkg: requested operation requires superuser privilege

??? i am the only computer user...what do i do?

use sudo:
```

sudo dpkg --configure -a

```

hth

---

