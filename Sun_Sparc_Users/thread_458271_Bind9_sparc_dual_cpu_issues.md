---
title: "Bind9 sparc dual cpu issues"
date: 2007-05-29
forum: Sun Sparc Users
---

### Post by yordin on 2007-05-29
All:

I have observed that Bind eventually fails miserably if let run free on a dual CPU Sparc.
(Feisty)
It seems that rndc aren't able to fully control named if it uses two worker threads.

I suspect that named second thread hangs on "rndc [reload|stop]" as well as if used as dyndns.

Workaround: Start it on one cpu adding the "-n1" option in /etc/default/bind9.

Rgrds:
/Y

---

### Post by netztier on 2007-10-28
> **yordin said:**
> All:

I have observed that Bind eventually fails miserably if let run free on a dual CPU Sparc.
(Feisty)
It seems that rndc aren't able to fully control named if it uses two worker threads.

I suspect that named second thread hangs on "rndc [reload|stop]" as well as if used as dyndns.

Workaround: Start it on one cpu adding the "-n1" option in /etc/default/bind9.

Rgrds:
/Y


Ah.. finally I've been able to un-dig your post, I had a vague memory that I had read a post about SMP and bind9. I have observed this as well on a Ultra2 with a recently installed feisty.

*Edit: using the -n1 option did help to have a stable DNS at our LoCo Team's Gutsy Gibbon release party :-)*

I'll try your suggestion now.

Do you have some more information about this, a bug report or something?


best regards

Marc

---

