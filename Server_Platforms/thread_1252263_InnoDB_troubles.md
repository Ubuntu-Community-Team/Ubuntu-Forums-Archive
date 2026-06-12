---
title: "InnoDB troubles"
date: 2009-08-28
forum: Server Platforms
---

### Post by The Keeper on 2009-08-28
I'm having big trouble with Ubuntu as well as Debian Lenny with MySQL InnoDB tables.

InnoDB is enabled by default, but when I go and look at enabled/supported engines (like in phpmyadmin), it says InnoDB is not enabled. After searching I found that running rm -rf /var/lib/mysql/ibdata*, rm -rf /var/lib/mysql/ib_logfile* and /etc/init.d/mysql restart fixes the problem.

It sure did, but only temporarily! Occasionally if mysqld or server itself is restarted, InnoDB is disabled again unless I run above commands again, which obviously destroys all InnoDB data.

What I can do to fix this permanently?

---

### Post by bottomless on 2010-03-12
I had the same problem where InnoDB would silently not start.

Make sure your innodb_buffer_pool_size parameter in /etc/mysql/my.cnf is not too high.

Here's the detailed explanation:
[http://blog.bottomlessinc.com/2010/03/innodb-engine-disabled-when-specifying-a-buffer-pool-size-too-high/](http://blog.bottomlessinc.com/2010/03/innodb-engine-disabled-when-specifying-a-buffer-pool-size-too-high/)

PlF

---

