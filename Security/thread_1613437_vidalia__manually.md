---
title: "vidalia  manually"
date: 2010-11-04
forum: Security
---

### Post by tony van on 2010-11-04
I finally got vidalia tor and polipo to work and all three ports 8118 9050 abd 9051 are working.
my mistake was in polipo ,i had to set the 8118 port. i removed privoxy cause i was getting a 
no logfile found. 
 
so here is my problem.
vidalia will only start manually is there a way using bum or sysv-rc-conf.
how would i load it ?
help appreciated.:)

---

### Post by tony van on 2010-11-05
even an idiot like me was able to figure this one out over time :P.
install polipo , with the required changes in the /etc/polipo/config and tor button
then go to open sysv-rc-conf and add for tor and polipo to start at boot.
vidalia is not needed. i tested it  via check.torproject.org and it worked.

---

### Post by CharlesA on 2010-11-05
Mark the thread as solved from the thread tools menu, if it's solved. :)

Thanks.

---

