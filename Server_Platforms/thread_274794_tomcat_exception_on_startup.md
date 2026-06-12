---
title: "tomcat exception on startup"
date: 2006-10-10
forum: Server Platforms
---

### Post by nkassi on 2006-10-10
I'm trying to setup Tomcat5 from the repository. I'm using the JDK packages that I downloaded from sun. Everytime I access the webapp it shows a blank page and the following line appears in the logs:

> 
Oct 10, 2006 11:32:46 AM org.apache.tomcat.util.threads.ThreadPool$ControlRunnable run
SEVERE: Caught exception (java.lang.NullPointerException) executing org.apache.jk.common.SocketConnection@719f1f, terminating thread



 I must restart tomcat5 afterwards or the page just hangs.

Is there something I forgot ?

Thanks in advance.

Nic

---

