---
title: "server upgrade 11.10 -&gt; 12.04 stuck in loop, won't complete"
date: 2012-04-28
forum: Server Platforms
---

### Post by rgeddes on 2012-04-28
upgrading a server, the install screen has been stuck for about 1 hour on this line:
```
Installing new version of config file /etc/apparmor.d/usr.sbin.mysqld ...
```

The following messages repeat on /var/log/syslog:
```
Apr 28 23:36:59 spitfire kernel: [256653.237623] init: mysql main process (5617) terminated with status 1
Apr 28 23:36:59 spitfire kernel: [256653.237828] init: mysql main process ended, respawning
Apr 28 23:37:00 spitfire kernel: [256654.251762] init: mysql post-start process (5618) terminated with status 1
Apr 28 23:37:00 spitfire kernel: [256654.345054] type=1400 audit(1335670620.941:3844): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=5672 comm="apparmor_parser"
Apr 28 23:37:03 spitfire kernel: [256656.660175] init: mysql main process (5676) terminated with status 1
Apr 28 23:37:03 spitfire kernel: [256656.660383] init: mysql main process ended, respawning
Apr 28 23:37:04 spitfire kernel: [256657.679800] init: mysql post-start process (5677) terminated with status 1
Apr 28 23:37:04 spitfire kernel: [256657.763986] type=1400 audit(1335670624.357:3845): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=5731 comm="apparmor_parser"
```

Any ideas how to complete the upgrade?

Thanks
R

RESOLVED:
I had mysql-proxy running, which somehow put the upgrade program in a loop.  I stopped mysql-proxy:
```
sudo service mysql-proxy stop
```
and the upgrade program continued on to complete the upgrade

---

