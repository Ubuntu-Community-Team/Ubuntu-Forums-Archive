---
title: "MySQL 5.1 problems after upgrading to Lucid 10.04"
date: 2010-05-05
forum: Server Platforms
---

### Post by servous on 2010-05-05
Yesterday I upgraded my server from Ubuntu 9.10 (64-bit) to Ubuntu 10.04 (using do-release-upgrade). Everything went smooth, except from that the MySQL server won't start anymore. And I can't start/stop/restart the service, neither from /etc/init.d/mysql restart, service mysql restart or restart mysql. The prompt just "freezes".

I've tried all tips on [http://newyork.ubuntuforums.org/showthread.php?t=1467115](http://newyork.ubuntuforums.org/showthread.php?t=1467115), without success.

I've also tride to completely remove the MySQL-server and re-install it from tasksel, which seemed to work - until I restarted the server. Then MySQL refuses to start again.

There is also no pid in /var/run/mysqld.

[EDIT]
I found a solution that worked for me at:
[http://ubuntuforums.org/showpost.php?p=9177875&postcount=6](http://ubuntuforums.org/showpost.php?p=9177875&postcount=6)
[/EDIT]

---

