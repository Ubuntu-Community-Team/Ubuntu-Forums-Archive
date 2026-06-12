---
title: "Gnome-shell (3.4.1-0ubuntu1) - no panels"
date: 2012-04-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-04-18
Todays new gnome-shell (3.4.1-0ubuntu1) update breaks the desktop panels leaving only background left.
I am not at my PC now, so I cannot test a fresh update [FONT=monospace]of [/FONT]gnome-shell (3.4.1-0ubuntu2).

In the version 3.4.1 there is a transition (dependency) from the package gir1.2-gjs-1.0 to this one:
gir1.2-gjsdbus-1.0.

---

### Post by kc1di on 2012-04-18
If by chance your using Nvidia current drivers on that machine there is a bug in the current compiz updates that breaks Nvidia so what you discribe happens in both unity and gnome 3 shell.. 

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/980298]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/980298")

---

### Post by sgage on 2012-04-18
> **Harry33 said:**
> Todays new gnome-shell (3.4.1-0ubuntu1) update breaks the desktop panels leaving only background left.
I am not at my PC now, so I cannot test a fresh update [FONT=monospace]of [/FONT]gnome-shell (3.4.1-0ubuntu2).

In the version 3.4.1 there is a transition (dependency) from the package gir1.2-gjs-1.0 to this one:
gir1.2-gjsdbus-1.0.

3.4.1-0ubuntu2 is working fine here. And the new libmutter fixed my desktop glitch on resetting the shell. Now if we could only get VT's with the proprietary nvidia drivers...

---

### Post by Harry33 on 2012-04-18
Right, the update gnome-shell_3.4.1-0ubuntu2 solves this issue for the Gnome-shell DE.

---

### Post by Quackers on 2012-04-18
Yes, working fine here and no more GS crashes after using synaptic :-)

---

