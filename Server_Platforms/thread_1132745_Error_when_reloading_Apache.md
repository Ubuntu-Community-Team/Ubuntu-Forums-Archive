---
title: "Error when reloading Apache"
date: 2009-04-22
forum: Server Platforms
---

### Post by botfish on 2009-04-22
Hi,

My Apache error log logs a large number of the following errors when ever I reload Apache configuration with /etc/init.d/apache2 reload. I'm running Apache/2.2.4

> 
[Wed Apr 22 21:38:27 2009] [notice] Graceful restart requested, doing restart
[Wed Apr 22 21:38:27 2009] [error] [client 127.0.0.1] (22)Invalid argument: apr_global_mutex_lock(rewrite_log_lock) failed
[Wed Apr 22 21:38:27 2009] [error] [client 127.0.0.1] (22)Invalid argument: apr_global_mutex_unlock(rewrite_log_lock) failed
 ... more of the above ...
[Wed Apr 22 21:36:47 2009] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.5 configured -- resuming normal operations


regards

---

