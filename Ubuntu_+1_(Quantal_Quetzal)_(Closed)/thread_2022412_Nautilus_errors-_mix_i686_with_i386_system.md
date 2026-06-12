---
title: "Nautilus errors- mix i686 with i386 system?"
date: 2012-07-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by critin on 2012-07-10
For several days nautilus has been closing with an error.  I've upgraded it's suggestions but still closed off and on.  When I used the classic mode the ctrl/alt/T wouldn't work, and none of the files had the close,minimize,max buttons showing.  I closed from the bottom task bar by right click.  kernel 3.5.3. failed on upgrading.  This A.M. I upgraded something ? through 'broken pkges' in synaptic and kernel 3.5.o.3.4 installed.
[ATTACH]221044[/ATTACH]
Nautilus still errored out, Ctrl/alt/T still didn't work.

This P.M.  I opened the error message and really searched. The error was in gnome panel.  I found a section that showed a i686 entry in the Stacktrace sig.  Mine is a i386 machine.  It gave me 4 things to upgrade, they are among the list in Stacktrace in the image.  After upgrading, things are working okay in classic.

Is including a i686 among all the i386's a normal thing to do?  Or is (was) it an (the)  error?

ctrl/alt/T worked normally in 2D at all times.

Thanks,

---

