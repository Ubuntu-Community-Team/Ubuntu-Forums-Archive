---
title: "libdb5.3 removable ?"
date: 2013-03-25
forum: Ubuntu Development Version
---

### Post by dino99 on 2013-03-25
both lidb5.1 & 5.3 are installed, and strangely 5.3 is set as removable (inside synaptic). Usually we use the latest version, not the previous one.

in fact that change comes from libpython2.7-stdlib:

python2.7 (2.7.4~rc1-2) experimental; urgency=low

  * Backport webbrowser updates from 3.3. Closes: #700429.
  * Build again using db-5.1 instead of db-5.3.

 -- Matthias Klose <doko@debian.org>  Sun, 24 Mar 2013 18:27:57 +0100

---

### Post by zika on 2013-03-25
> **dino99 said:**
> both lidb5.1 & 5.3 are installed, and strangely 5.3 is set as removable (inside synaptic). Usually we use the latest version, not the previous one.Something went wrong in dependencies: if I try to remove libdb5.1 lot of stuff gets labeled for removal also... If I try the same with 5.3 it would go smoothly... Transition I suppose...

---

### Post by Harry33 on 2013-03-25
> **zika said:**
> Something went wrong in dependencies: if I try to remove libdb5.1 lot of stuff gets labeled for removal also... If I try the same with 5.3 it would go smoothly... Transition I suppose...

Python 2.7 is now rebuilt agains libdb5.1. The former update was built against libdb5.3.
So, this means you can safely remove (or purge) libdb5.3.

---

### Post by zika on 2013-03-25
> **Harry33 said:**
> Python 2.7 is now rebuilt agains libdb5.1. The former update was built against libdb5.3.
So, this means you can safely remove (or purge) libdb5.3.
Makes sense... Thank You...
Already purged couple of hours ago...

---

### Post by dino99 on 2013-03-25
but the main question is : why using that old version now ?

---

### Post by Harry33 on 2013-03-25
> **dino99 said:**
> but the main question is : why using that old version now ?

Obviously libdb5.3 is newer, but in order to switch to that new ABI, it would mean rebuilding a lot of packages in RR.
And not to mention all the compatibility testing.
Not a good idea to go into that at this stage.

---

