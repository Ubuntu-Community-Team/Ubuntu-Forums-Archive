---
title: "cron triggers segfault on php script"
date: 2012-11-14
forum: Server Platforms
---

### Post by Darghon on 2012-11-14
Hi all,

I have a home server installed with ubuntu 12.04 server edition.

I made a php script that checks a folder for specific files and moves them if found.

script works perfectly if I execute it through command line.
But when I add it to my crontab (root) it triggers segfault.
Several hours of googling has resulted in 0 answers, so I hope experts here can help me.

The triggered fault:
```

Nov 14 21:44:01 Sapprim kernel: [393321.224967] cron[9138]: segfault at 3dae8eb7f889 ip 00007fae8f5878d0 sp 00007ffff5a81668 error 4 in ld-2.15.so[7fae8f56f000+22000]

```
The crontab -l =>
```

*/15 * * * * /usr/bin/php5 /media/processSeries.php > /debug.txt

```

no logs are created in debug.txt
php -v
```

PHP 5.3.10-1ubuntu3.4 with Suhosin-Patch (cli) (built: Sep 12 2012 18:59:41) 

```
Any help is definately appreciated, and if any more info is needed, ask and you shall receive.

---

