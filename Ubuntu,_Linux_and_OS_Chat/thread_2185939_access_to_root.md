---
title: "access to root"
date: 2013-11-05
forum: Ubuntu, Linux and OS Chat
---

### Post by salehi.information on 2013-11-05
hi dears,
i'm new user pf ubuntu OS,so i have two question??
why "su" and "sudo" commands need to be Set-UID programs??
What will happen if they are not? 
thanks

---

### Post by 3rdalbum on 2013-11-05
Setuid flag means "This program always runs as the program's owner instead of the user". Su and Sudo are setuid and owned by root.

Think about it; if they did not run as root, how could they run anything else as root?

---

