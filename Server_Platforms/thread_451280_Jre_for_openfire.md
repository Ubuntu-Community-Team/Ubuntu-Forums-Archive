---
title: "Jre for openfire"
date: 2007-05-22
forum: Server Platforms
---

### Post by elias85 on 2007-05-22
i ve installed openfire on ubuntu 6.06 and the o/s cant find where the java version i ve installed is.. i ve tried modifying the /root/.bashrc file 

i added 
PATH=$PATH:$HOME/bin:/opt/jdk1.6.0_01/bin
export INSTALL4J_JAVA_HOME=/opt/jdk1.6.0_01/bin

at the end of the file, logged out, and logged in again and still nothing (when im trying to execute /opt/openfire/bin/openfire) . i still get the message 
"No suitable Java Virtual Machine could be found on your system.
The version of the JVM must be at least 1.5.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file /root/.install4j "
Any help?

---

