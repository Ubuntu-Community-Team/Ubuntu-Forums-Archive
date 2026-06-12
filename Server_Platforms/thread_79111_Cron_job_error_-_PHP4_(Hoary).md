---
title: "Cron job error - PHP4 (Hoary)"
date: 2005-10-19
forum: Server Platforms
---

### Post by ScatterBrain on 2005-10-19
I've got a Hoary web server that runs PHP4.  After an upgrade yesterday, I've been getting these notifications from the cron daemon.  Can someone explain them to me?

```

From: 	Cron Daemon <root@columbia.klcollins.org>
To: 	root@columbia.klcollins.org
Subject: 	Cron <root@columbia>   [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm
Date: 	Wed, 19 Oct 2005 15:09:01 -0400 (EDT)


xargs: rm: terminated by signal 11

```

Thanks in advance.

---

