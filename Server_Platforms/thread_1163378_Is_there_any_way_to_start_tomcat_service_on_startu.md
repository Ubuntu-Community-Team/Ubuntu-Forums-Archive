---
title: "Is there any way to start tomcat service on startup as non-root?"
date: 2009-05-18
forum: Server Platforms
---

### Post by akhan on 2009-05-18
Is there any way to start tomcat service on startup as non-root?
 
-Ak

---

### Post by John Cheng on 2009-05-18
Yes, if you are ok with Tomcat listening on non-privileged ports (1024+). Assuming it is installed at /opt/tomcat, you should be able to start it as a non-root user with:

```
/opt/tomcat/bin/startup.sh
```

If you are depending on the [FONT="Courier New"]/etc/init.d/ [/FONT]scripts to start it, you will have to modify it so that the tomcat script runs the start command using the [FONT="Courier New"]su -c[/FONT] command. For example:

```
su -s /bin/bash - $TOMCAT_USER -c "/opt/tomcat/bin/startup.sh"

```

---

