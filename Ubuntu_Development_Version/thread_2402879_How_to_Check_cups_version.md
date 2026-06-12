---
title: "How to Check cups version"
date: 2018-10-05
forum: Ubuntu Development Version
---

### Post by damian.jacob on 2018-10-05
Hi,
is there any way to check what version of cups is running on ubuntu?

---

### Post by PaulW2U on 2018-10-05
In a web browser: **[http://127.0.0.1:631/](http://127.0.0.1:631/)**
or in a terminal: **apt policy cups**

---

### Post by slickymaster on 2018-10-05
Check in the Documentation/Help tab of the web interface: [http://localhost:631/](http://localhost:631/)

 Also, Distrowatch will show you which versions are in which distributions, eg [http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)

---

### Post by damian.jacob on 2018-10-05
Thanks, apt-cache policy worked!

---

