---
title: "Trouble in upgrade..."
date: 2012-09-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by zika on 2012-09-18
```
Setting up python3-pyatspi2 (2.5.92+dfsg-0ubuntu1) ...
  File "/usr/lib/python3/dist-packages/examples/magFocusTracker.py", line 285
    print 'Magnification service not available. Exiting.'
                                                        ^
SyntaxError: invalid syntax

dpkg: error processing python3-pyatspi2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-orca:
 gnome-orca depends on python3-pyatspi2 (>= 2.1.90); however:
  Package python3-pyatspi2 is not configured yet.

dpkg: error processing gnome-orca (--configure):
 dependency problems - leaving unconfiguredNo apport report written because the error message indicates its a followup error from a previous failure.

Errors were encountered while processing:
 python3-pyatspi2
 gnome-orca
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by dino99 on 2012-09-18
already fixed, coming on the way  ):P

---

### Post by zika on 2012-09-18
> **dino99 said:**
> already fixed, coming on the way  ):P
Solved: print 'Magnification service not available. Exiting.' -> print ('Magnification service not available. Exiting.')
):P

---

