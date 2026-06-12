---
title: "Ubuntu server 10.04 processes question"
date: 2012-01-09
forum: Server Platforms
---

### Post by raczzoli on 2012-01-09
Hello.

We have a dedicated dell poweredge r200 with ubuntu server 10.04. We keep on this server a php+mysql application developed by our company. The problem is, when too many clients connect to the server at the same time, or when a client calls a service which uses a lot of resources (memory or cpu) the server freezes, and we are not even able to log into ssh anymore to kill the process. The server responds to pings for a little while but after a few minutes it fails completely, and we need to call to the data center and request a hard reset. 

If we look at the syslog, it says that the process (apache or mysql) has eaten up all the available resources (memory usage 100%, cpu the same, swap space the same.), and probably after that crashes the server.

Is there any possibility to limit how much a process can use from the system resources, and if it exeeds the limit, automatically kill it or restart the service? I know the resource limits can be set from the configuration file of the services (for example if a php script takes more than 60 seconds to execute it can be terminated automatically), but is there any way to set a general limit for any process to protect the server from crashing. Lets say if an application uses 100% cpu for more than 5 seconds kill it?

Thank you.

---

