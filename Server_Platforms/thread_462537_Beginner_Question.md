---
title: "Beginner Question"
date: 2007-06-02
forum: Server Platforms
---

### Post by tj71587 on 2007-06-02
How would i go about setting up an ftp on my apache directory?

Thanks,

T.J.

---

### Post by pbw on 2007-06-04
install proftpd, add a user to your ftp group and edit proftpd.conf to set default root to your apache directory (/var/www if you havent changed it)

---

