---
title: "postgresql-8.1 .deb problems"
date: 2006-09-28
forum: Repositories &amp; Backports
---

### Post by pstep9407 on 2006-09-28
Hello: I hope this is the right area to post this question. I am working with the Ubuntu GIS packages (great work, by the way!) and I'm having an issue with the postgresql install. Below is the terminal response. Thanks for your help.

```


Setting up postgresql-8.1 (8.1.4-0ubuntu1) ...
 * Starting PostgreSQL 8.1 database server  * The PostgreSQL server failed to start. Please check the log output:
LOG:  could not load root certificate file "root.crt": No SSL error reported
DETAIL:  Will not verify client certificates.
LOG:  could not translate host name "localhost", service "5432" to address: Name or service not known
WARNING:  could not create listen socket for "localhost"
FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.1, action "start" failed.
dpkg: error processing postgresql-8.1 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql-plpython-8.1:
 postgresql-plpython-8.1 depends on postgresql-8.1; however:
  Package postgresql-8.1 is not configured yet.
dpkg: error processing postgresql-plpython-8.1 (--configure):
 dependency problems - leaving unconfigured

```

---

### Post by pstep9407 on 2007-03-05
So, months later, and updates to the postgres package, but still nothing. Does anyone have a clue as to what I need to do?


```
Setting up postgresql-8.1 (8.1.8-0ubuntu6.06.1) ...
 * Starting PostgreSQL 8.1 database server  * The PostgreSQL server failed to start. Please check the log output:
LOG:  could not translate host name "localhost", service "5432" to address: Name or service not known
WARNING:  could not create listen socket for "localhost"
FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.1, action "start" failed.
dpkg: error processing postgresql-8.1 (--configure):
 subprocess post-installation script returned error exit status 1
```

---

### Post by Yv12345vY on 2007-03-26
I had to install postgres-8.0.  Maybe once I get this running I'll be able to upgrade to 8.1

---

