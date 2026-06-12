---
title: "(apache*2)^2"
date: 2005-12-09
forum: Server Platforms
---

### Post by Razvan on 2005-12-09
Hi Guys!

```
martin@martin:~$ ps -d
  PID TTY          TIME CMD
[snip]
 7588 ?        00:00:00 apache2
 7589 ?        00:00:00 apache2
 7590 ?        00:00:00 apache2
 7591 ?        00:00:00 apache2
 7592 ?        00:00:00 apache2
[snip]
 7686 ?        00:00:00 apache2
 7687 ?        00:00:00 apache2
 7688 ?        00:00:00 apache2
 7693 pts/0    00:00:00 ps
martin@martin:~$

```

is it usual for apache to run 8 times? this is on a home box for testing/playing purposes. i was the only one who acessed the site at that moment.

thanks for input, Martin

---

### Post by blueplazma on 2005-12-09
Seems normal.  Apache2 launches many child threads.

---

