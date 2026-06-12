---
title: "mysql error: Can't create a new thread (errno 11);"
date: 2013-03-28
forum: Server Platforms
---

### Post by hunterlove22 on 2013-03-28
Hello everyone.

I have a db server running Percona Xtradb server, and 5 slaves. I always get the error

> [COLOR=#000000][FONT=verdana]mysql error: Can't create a new thread (errno 11); if you are not out of available memory, you can consult the manual for a possible OS-dependent bug[/FONT][/COLOR]

Though i set ulimited

> root@master:~# ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 2062915
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
[COLOR=#ff0000]open files                      (-n) 1000000[/COLOR]
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 1000000
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited




> root@master:~# cat /proc/`pidof mysqld`/limits | egrep "(processes|files)"Max processes             1000000              1000000              processes
Max open files            1000000              1000000              files




I really dont know what's going on? Please help me.

Thanks,

---

### Post by hunterlove22 on 2013-03-29
Please anyone helps me.

---

