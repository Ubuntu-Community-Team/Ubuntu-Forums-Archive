---
title: "MySQL server spews Error 24's after kernel upgrade on Monday."
date: 2014-10-21
forum: Server Platforms
---

### Post by ernied on 2014-10-21
Before yesterday, our MySQL server on our Ubuntu 14.04 LTS web server was working without issue. But with automatic updates turned on, I logged into the server on Monday, saw the kernel update and request to reboot the server, and dutifully rebooted the server.

When the server came back up, the server was running kernel "3.13.0-37-generic #64-Ubuntu SMP" and MySQL was giving us errors like this in place of our web pages:

ERROR 1018 (HY000): Can't read dir of '.' (errno: 24)

This means that MySQL doesn't have its ulimit -n set high enough to load all the files in /var/lib/mysql. I changed the limit in /etc/security/limits.conf like this:

mysql soft nofile 20000 
mysql hard nofile 25000

As there are only about 4400 files in /var/lib/mysql, this should be many times what MySQL needs to run. There are no other files in /etc/security/limits.d.

However, we're still getting these error messages from MySQL. We've deactivated our Ubuntu server and gone back to our backup server. Also, I've deactivated automatic updates, thank you very much.

---

