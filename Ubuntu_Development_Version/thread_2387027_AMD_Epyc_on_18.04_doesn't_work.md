---
title: "AMD Epyc on 18.04 doesn't work"
date: 2018-03-13
forum: Ubuntu Development Version
---

### Post by teagls on 2018-03-13
Hi,

I upgraded to 18.04 beta to try out the beta release on a dual socket Epyc 7281 server, but the system shuts down after 10 minutes. The system was originally on 17.10 and I experienced the same issue. In the grub command line I had to add "pti=off", this fixed the shutdowns on 17.10, but it doesn't work on 18.04 and the system continually shuts down each time after about 10 minutes.

---

