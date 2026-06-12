---
title: "Web Server slow"
date: 2013-02-12
forum: Server Platforms
---

### Post by alfirdaous on 2013-02-12
Hello all.

After reinstalling the web server, I found out that it is too slow, and queries are not submitted, I checked the error log:

```

[Tue Feb 12 15:22:14 2013] [warn] child process 9884 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:15 2013] [warn] child process 9676 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:15 2013] [warn] child process 9512 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:15 2013] [warn] child process 9688 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:15 2013] [warn] child process 9885 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:15 2013] [warn] child process 9886 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:15 2013] [warn] child process 10299 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:15 2013] [warn] child process 10304 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:15 2013] [warn] child process 10305 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:15 2013] [warn] child process 9128 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:15 2013] [warn] child process 9130 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:15 2013] [warn] child process 9895 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:17 2013] [warn] child process 9884 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:17 2013] [warn] child process 9676 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:17 2013] [warn] child process 9512 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:17 2013] [warn] child process 9688 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:17 2013] [warn] child process 9885 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:17 2013] [warn] child process 9886 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:17 2013] [warn] child process 10299 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:17 2013] [warn] child process 10304 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:17 2013] [warn] child process 10305 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:17 2013] [warn] child process 9128 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:17 2013] [warn] child process 9130 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:17 2013] [warn] child process 9895 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:18 2013] [warn] child process 9884 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:18 2013] [warn] child process 9676 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:18 2013] [warn] child process 9512 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:18 2013] [warn] child process 9688 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:18 2013] [warn] child process 9885 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:18 2013] [warn] child process 9886 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:18 2013] [warn] child process 10299 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:18 2013] [warn] child process 10304 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:18 2013] [warn] child process 10305 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:18 2013] [warn] child process 9128 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:18 2013] [warn] child process 9130 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:18 2013] [warn] child process 9895 still did not exit, sending a SIGTERM
[Tue Feb 12 15:22:20 2013] [error] child process 9884 still did not exit, sending a SIGKILL
[Tue Feb 12 15:22:20 2013] [error] child process 9130 still did not exit, sending a SIGKILL
[Tue Feb 12 15:22:21 2013] [notice] caught SIGTERM, shutting down
[Tue Feb 12 15:22:25 2013] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations

```

I have installed only: apache2, php5, mysql and phpmyadmin, when I launched the url (Server IP), it is going slow, even to get in phpmyadmin, it takes time

The partitions are like this (home directory is the content of the website, ONLY 1 website is there)

```

Filesystem      Size  Used Avail Use% Mounted on
rootfs           49G  4.0G   43G   9% /
/dev/root        49G  4.0G   43G   9% /
none            199M  2.7M  197M   2% /run
none            5.0M  4.0K  5.0M   1% /run/lock
none            995M     0  995M   0% /run/shm
/dev/sda2       879G  718G  118G  86% /home

```

Thanks for your help

---

### Post by tgalati4 on 2013-02-12
```
sudo apt-get install htop
htop
```

What processes are taking up the CPU? Control-C to exit.

---

### Post by alfirdaous on 2013-02-12
Thanks tgalati4, everything seems to be OK, one table has been crashed

---

