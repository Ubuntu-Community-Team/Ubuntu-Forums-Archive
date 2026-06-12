---
title: "Kill - Killall ..."
date: 2005-10-26
forum: Server Platforms
---

### Post by dbee on 2005-10-26
Why won't my system kill the mysqld_safe daemon on my computer ???

root@ubuntu:/usr/local/mysql/bin # ps
  PID TTY          TIME CMD
 6911 pts/0    00:00:00 bash
 7182 pts/0    00:00:00 mysqld_safe
 7377 pts/0    00:00:00 ps
root@ubuntu:/usr/local/mysql/bin # killall mysqld_safe
root@ubuntu:/usr/local/mysql/bin # kill 7182
root@ubuntu:/usr/local/mysql/bin # ps
  PID TTY          TIME CMD
 6911 pts/0    00:00:00 bash
 7182 pts/0    00:00:00 mysqld_safe
 7385 pts/0    00:00:00 ps

---

### Post by heimo on 2005-10-26
How about *kill -9 $(pidof mysqld_safe)* ?


EDIT: Or... 
/etc/init.d/mysql stop
:rolleyes:

---

### Post by LordHunter317 on 2005-10-26
He's running a local one, so it's doubtful that will actually work.  Knowing why it's hung would be nice, did you look at the logs?  What does ps axu say about state?

---

