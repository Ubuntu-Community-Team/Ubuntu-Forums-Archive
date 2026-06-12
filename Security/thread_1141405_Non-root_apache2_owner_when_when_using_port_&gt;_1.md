---
title: "Non-root apache2 owner when when using port &gt; 1024, possible?"
date: 2009-04-28
forum: Security
---

### Post by usmanaziz on 2009-04-28
Hi

I am using a router that redirects incoming port 80 requests to a port greater that 1024.

For my Ubuntu 9.04 server install, using the default LAMP install,  the apache2  is started as root and the apache PID in /var/run/ is owned by root.

Is it possible to remove all traces of root ownership so that the whole apache2 server starts and runs as the www-data user, given that I do not run it on port 80?

Can somebody tell me - from a security point of view, is it worth trying to get the apache server to run entirely as a non-root user, or am I wasting time?


Thank you
Usman

---

### Post by bodhi.zazen on 2009-04-28
apache is started by root, but the chid processes then run as www-data

```
ps aux | grep apache2
```

See all the "www-data" ???

You can change the port by changing /etc/apache2/ports.conf

---

