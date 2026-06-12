---
title: "PostgreSQL not starting at boot &amp; httpd"
date: 2010-05-12
forum: Server Platforms
---

### Post by Oasu4g on 2010-05-12
Hello,

I am trying to get SQL-Ledger installed and running on my computer, which needs PostgreSQL installed to run. Currently, I am having trouble with it starting at boot-up. How can I access the appropriate log files in order to figure out what's wrong?

Also, I need to know what httpd is, and who the owner and groups using that might be on my system.

Thanks for any help, and I hope I've made things clear enough.

Regards,

Tim

---

### Post by windependence on 2010-05-12
The source comes with a startup script that can be installed by  running: 
```
# cp contrib/start-scripts/linux /etc/init.d/postgresql
# update-rc.d postgresql defaults
```
(update-rc.d is to debian-based systems what chkconfig is to  Redhat-based systems).

The logs should be in /var/log.

-Tim

---

### Post by Oasu4g on 2010-05-13
Here is the log output. Unfortunately it means nothing to me. I'm very new to this.

```
2010-05-12 20:41:49 CDT FATAL:  could not create shared memory segment: Invalid argument
2010-05-12 20:41:49 CDT DETAIL:  Failed system call was shmget(key=5432001, size=38207488, 03600).
2010-05-12 20:41:49 CDT HINT:  This error usually means that PostgreSQL's request for a shared memory segment exceeded your kernel's SHMMAX parameter.  You can either reduce the request size or reconfigure the kernel with larger SHMMAX.  To reduce the request size (currently 38207488 bytes), reduce PostgreSQL's shared_buffers parameter (currently 4096) and/or its max_connections parameter (currently 103).
	If the request size is already small, it's possible that it is less than your kernel's SHMMIN parameter, in which case raising the request size or reconfiguring SHMMIN is called for.
	The PostgreSQL documentation contains more information about shared memory configuration.
```

I installed the software through the repos. My OS version is 9.04.

Thanks for your help windependence!

Regards,

Tim

---

### Post by Oasu4g on 2010-05-14
Should I download the source code and run that script you mentioned?

---

### Post by Oasu4g on 2010-05-22
I tried [this](http://dancingpenguinsoflight.com/2010/03/dealing-with-could-not-create-shared-memory-segment-from-postgres-on-ubuntu/), and it seemed to work. I don't know if it's the best fix out there though. Could someone explain what this does? Is it the best fix for my problem?

---

