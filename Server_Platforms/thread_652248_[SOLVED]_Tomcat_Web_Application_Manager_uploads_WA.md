---
title: "[SOLVED] Tomcat Web Application Manager uploads WAR to wrong folder"
date: 2007-12-28
forum: Server Platforms
---

### Post by Kzin on 2007-12-28
Hello again,
As the title of this aptly-named post implies, I have installed tomcat 5.5 with no problems at all.  Its up and running, and I can see the test pages and access the manager just fine.

By default, tomcat created /usr/share/tomcat5.5 and /usr/share/tomcat5.5-webapps, the latter of which contains the precompiled test pages, manager and the etc.  So it would seem that is my root, as it were.

So I go into the manager, upload a war file, but it uploads the file to /usr/share/tomcat5.5/webapps which is a symlink to /var/lib/tomcat5.5/webapps invariably causing the war file not to deploy correctly.

What would cause the manager to think the server was running in a different place than it is?  Or am I just missing a step or something?

```
cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

uname -r
2.6.22-14-server

```

peace

---

### Post by Kzin on 2008-01-03
bump

---

### Post by Kzin on 2008-01-03
I have actually found this problem to be what seems to be not a problem.  
I found the log files and the web.xml is stopping the application from working properly.  So I guess the manager expects the application to work, and will not deploy broken code. :'(

---

