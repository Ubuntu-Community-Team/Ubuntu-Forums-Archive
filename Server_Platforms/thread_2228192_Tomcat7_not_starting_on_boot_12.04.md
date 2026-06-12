---
title: "Tomcat7 not starting on boot 12.04"
date: 2014-06-06
forum: Server Platforms
---

### Post by Danny_R on 2014-06-06
Morning

when i restart my 12.04 server tomcat does not start automatically

if i run 

```
/opt/tomcat-7.0.54/bin/startup.sh &
```

i get

```
[1] 2669
root@pbx-2:~# using CATALINA_BASE: /opt/tomcat7.0.54
using CATALINA_HOME: /opt/tomcat-7.0.54
using CATALINA_TMPDIR: /opt/tomcat-7.0.54/temp
using JRE_HOME: /usr
using CLASSPATH: /opt/tomcat-7.0.54/bin/bootstrap.jar:/opt?tomcat-7.0.54/bin/tomcat-juli.jar
Tomcat started
```

please bare with me as i only started using Ubuntu about 4 days ago.....

will i need to add a script somewhere to get tomcat to be fire at boot

thanks

---

### Post by Toz on 2014-06-06
One quick way is to add:
```
/opt/tomcat-7.0.54/bin/startup.sh
```
...to **/etc/rc.local** above the *exit 0* command. This file runs as the last item during the boot phase.

---

### Post by Danny_R on 2014-06-06
Awesome!

thats what i was looking for thanks

---

