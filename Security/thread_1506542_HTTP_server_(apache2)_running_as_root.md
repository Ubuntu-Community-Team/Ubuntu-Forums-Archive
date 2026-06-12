---
title: "HTTP server (apache2) running as root"
date: 2010-06-10
forum: Security
---

### Post by borepstein on 2010-06-10
Hi all,

I've got Ubuntu 10 running here and have just discovered that the processes for the HTTP server (apache2) appear to run as user root as opposed to user apache/www/whatever as is custom on most other Linux/Unix distros. Why would that be? Seems very insecure to me.

Boris.

---

### Post by FuturePilot on 2010-06-10
Apache on Ubuntu runs as www-data. Did you change something?

---

### Post by bodhi.zazen on 2010-06-10
> **borepstein said:**
> Hi all,

I've got Ubuntu 10 running here and have just discovered that the processes for the HTTP server (apache2) appear to run as user root as opposed to user apache/www/whatever as is custom on most other Linux/Unix distros. Why would that be? Seems very insecure to me.

Boris.

Can you post the output you are looking at please so we can see what you are asking about.

---

### Post by invader.sushil on 2011-08-03
> **bodhi.zazen said:**
> Can you post the output you are looking at please so we can see what you are asking about.
I am hosting webserivces  on apache2 in ubuntu10. I want to start the apache2 as root and then the service should run as the user www-data. The processes running are reproduced below -
 
USER           PID     CPU  MEM  VSZ     RSS  TTY  STAT   START  TIME      COMMAND
root             2824    0.0    0.1   8104   3752   ?     Ss       08:37   0:00   /usr/sbin/apache2 -k start
www-data    2824    0.0    0.1   8104   3752   ?     Ss       08:37    0:00  /usr/sbin/apache2 -k start
www-data    2824    0.0    0.1   8104   3752   ?     Ss       08:37    0:00  /usr/sbin/apache2 -k start
www-data    2824    0.0    0.1   8104   3752   ?     Ss       08:37  0:00   /usr/sbin/apache2 -k start
 
Continuing to run apache2 as root might not be secure thus i want that once the apache2 starts as root it should then move down to continue runing as the user www-data and it stop for user root.

---

### Post by bodhi.zazen on 2011-08-03
Take a look at how apache works ;)

The parent server runs as root and spawns child processes which run as www-data

The child processes are the ones listening for connections and doing the work, not the parent server.

> While the parent process is usually started as root under Unix in order to bind to port 80, the child processes and threads are launched by Apache as a less-privileged user.

See:

[http://httpd.apache.org/docs/2.2/mod/prefork.html](http://httpd.apache.org/docs/2.2/mod/prefork.html)

[http://httpd.apache.org/docs/2.2/mod/worker.html](http://httpd.apache.org/docs/2.2/mod/worker.html)

---

### Post by thewanderer on 2011-08-03
That root process is the parent Apache process. 

It is required to be root so that Apache can bind to port 80 (a privileged port).

The parent process does not serve any requests, so is not inherently insecure.

---

