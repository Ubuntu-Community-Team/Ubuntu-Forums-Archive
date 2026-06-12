---
title: "[SOLVED] Tomcat5.5 doesn't write logfiles in Hardy"
date: 2008-05-21
forum: Server Platforms
---

### Post by PaulHuygen on 2008-05-21
I installed tomcat5.5, tomcat5.5-admin and tomcat5.5-webapps. It seems to work, but /var/log/tomcat5.5 remains empty and so does /usr/share/tomcat5.5/logs. Does anybody know how I can get logfiles back?

Thanks,

Paul Huygen

---

### Post by PaulHuygen on 2008-05-22
I can answer this question myself: I had made a mess of java-packages. As a result /etc//alternatives pointed to binaries that belonged to another java-distribution than the one in the JAVA_HOME environment parameter.

---

