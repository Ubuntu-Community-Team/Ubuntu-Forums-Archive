---
title: "Why Tomcat can not delete its pid file?"
date: 2020-09-14
forum: Server Platforms
---

### Post by paperring on 2020-09-14
I installed Tomcat 9.0.37 on Ubuntu 18.04 VPS. Problem is after starting the Tomcat, it makes inactive itself automatically after sometimes and when active state gives a status notification like this:


    ```
Starting Tomcat 9 servlet container...
    Sep 14 14:23:55 ubuntuServer startup.sh[23466]: Existing PID file found during start.
    Sep 14 14:23:55 ubuntuServer startup.sh[23466]: Removing/clearing stale PID file.
    Sep 14 14:23:55 ubuntuServer startup.sh[23466]: Tomcat started.
    Sep 14 14:23:55 ubuntuServer systemd[1]: Started Tomcat 9 servlet container.



```

I thougth that Tomcat can not delete its pid file when restarting but I can't find where the problem is. Here is "/etc/systemd/system/tomcat.service" file ("latest" directory is a symbolic link which will point tomcat installation directory):


    ```
[Unit]
    Description=Tomcat 9 servlet container
    After=network.target
    
    [Service]
    
    Type=forking
    User=tomcat
    Group=tomcat
    Environment="JAVA_HOME=/opt/jdk/jdk1.8.0_261"
    Environment="JAVA_OPTS=-Djava.security.egd=file:///dev/urandom"
    
    
    Environment="CATALINA_BASE=/opt/tomcat/latest"
    Environment="CATALINA_HOME=/opt/tomcat/latest"
    
    Environment="CATALINA_PID=/opt/tomcat/latest/temp/tomcat.pid"
    Environment="CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC"
    
    
    ExecStart=/opt/tomcat/latest/bin/startup.sh
    ExecStop=/opt/tomcat/latest/bin/shutdown.sh
    [Install]
    
    WantedBy=multi-user.target

```

Any idea to solving this?

---

### Post by TheFu on 2020-09-14
.system files run as root, then fork over to a different userid, tomcat, in this situation. There are reasons.

I suspect you might be confusing the process, euid and egid.
What are the file permissions for /opt/tomcat/latest/temp/tomcat.pid? Owner, group, and full permissions?
What are the directory permissions for /opt/tomcat/latest/temp/?  Owner, group, and full permissions?

The parent directory permissions control whether a file inside can be deleted. This is Unix 101 stuff.

I know very little about Java anymore. Have avoided it since around 1996. Still waiting for the promises made to become true about that language and environment.

---

### Post by paperring on 2020-09-14
Directory permissions:
```
drwxrwx--- 2 tomcat tomcat 4096 Sep 14 21:27 temp
```
File permissions:
```
[FONT=monospace][COLOR=#000000]-rw-r----- 1 tomcat tomcat    5 Sep 14 21:27 tomcat.pid[/COLOR][/FONT]
```
Everytime I execute shutdown.sh and startup.sh tomcat.pid file permissions change as above and gives > Existing PID file found during start. status message.
I see your reasons you're right. I'am learning spring framework and I'am just practicing on servlet api.

---

