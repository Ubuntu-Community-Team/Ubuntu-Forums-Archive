---
title: "need to know where to place faxgetty on startup  at on 8.04.3 TLS server"
date: 2009-08-13
forum: Server Platforms
---

### Post by kustomjs on 2009-08-13
Hey Guys
could anybody tell me where to place faxgetty on startup at on 8.04.3 TLS?

---

### Post by lensman3 on 2009-08-13
Try putting your private startup scripts in "/etc/rc.d/local.rc".  This was originally used in Unix specifically for starting local services.  One my firewall system, I use it for starting fetchmail.  The script runs as "root".  

I also use it to at the start up to tweak ifconfig -> /sbin/ifconfig eth0 txqueuelen 100

I change the text queue length to something shorter so the Ethernet doesn't stall out when the buffers are full.  It give a better response keeping a fast throughput, but with a little more interrupt overhead.

You can also put it into the SYS 5 start up with /etc/init.d and the /etc/rc?.d setup.

Hope this helps.

---

