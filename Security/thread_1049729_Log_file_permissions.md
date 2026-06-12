---
title: "Log file permissions"
date: 2009-01-24
forum: Security
---

### Post by herbie643 on 2009-01-24
I'm trying to make my system a bit more secure... So can you change the permissions in /var/log directory to have ROOT only access?  Does it hamper or stop other processes from logging?

---

### Post by x33a on 2009-01-24
afaik, you shouldn't mess with permissions of system specific files.

---

### Post by cariboo on 2009-01-25
If you check ownership and permissions, you will see most of the log files are owned by root, or the daemon that created the logs. Just leave them the way the are, as you have to me root to edit the log files.

Jim

---

