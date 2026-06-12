---
title: "Adding a system account for tomcat"
date: 2007-06-20
forum: Server Platforms
---

### Post by matt_b on 2007-06-20
I've installed [confluence]("http://www.atlassian.com/software/confluence/") on my server, which uses tomcat as the application server. Tomcat is not "installed" in the typical *apt-get* sense, all of confluence's files (including tomcat) live in */opt* so there are no scripts in */etc/init.d* to allow me to start it up and shut it down with the system. Consequently, I want to make my own...

I know I can create a script in */etc/init.d* which calls confluence's startup script (in */opt/confluence/bin/startup.sh*), but I don't want tomcat to be started as root - I think I need to call this script via *su someuser /opt/confluence/bin/startup.sh * to get the process launched as a non-privileged user. Here comes the question...

How do I add a non-privileged user for the sole purpose of launching an application? Do I need to add a corresponding group (like *www-data* in apache)? Do I give this user a password? Do I give them a home directory?

I'd appreciate any pointers..!
matt_b

---

### Post by matt_b on 2007-07-10
Sorry, have to bump this one...

How do I add a non-privileged user for the sole purpose of launching an application? Do I need to add a corresponding group (like www-data in apache)? Do I give this user a password? Do I give them a home directory?

---

