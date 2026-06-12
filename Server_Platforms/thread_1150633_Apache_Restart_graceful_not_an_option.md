---
title: "Apache Restart graceful not an option"
date: 2009-05-06
forum: Server Platforms
---

### Post by xkaliburx on 2009-05-06
Running on a CentOS 5 box, I can simply do an apache2 -k graceful which restarts apache in a graceful mode not just killing everyone.

I don't see that option in ubuntu-server 8.04.  I only see the following options;
* Usage: /etc/init.d/apache2 {start|stop|restart|reload|force-reload|start-htcacheclean|stop-htcacheclean|status}

I am wondering if there is an extra package you need, or is the reload command a similar thing that will reload the settings but not kill the existing threads.

---

### Post by Kareeser on 2009-05-06
Correct, reload will re-read all of the configuration files without killing and started processes.

---

