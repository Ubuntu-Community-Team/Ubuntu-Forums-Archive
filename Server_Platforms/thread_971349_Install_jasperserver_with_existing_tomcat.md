---
title: "Install jasperserver with existing tomcat"
date: 2008-11-04
forum: Server Platforms
---

### Post by bangeko on 2008-11-04
I never have happy ending install jasperserver with existing tomcat, the appication can't start. I tried linux-installer and WAR in 7.04, 7.10, 8.04 and 8.10. Anyone can help?

---

### Post by Dimas on 2008-11-25
I've the same problem... I've posted detailed information of that problem: [http://ph.ubuntuforums.com/showthread.php?t=977276](http://ph.ubuntuforums.com/showthread.php?t=977276)

---

### Post by bangeko on 2008-11-26
Success install jasperserver-3.1-linux-installer.bin with existing tomcat6 and mysql5 in hardy today.

---

### Post by Dimas on 2008-11-26
More detailed info please?

---

### Post by bangeko on 2008-11-27
> **Dimas said:**
> More detailed info please?

Still FAIL with sudo /etc/init.d/tomcat5.5 start but if you use /usr/share/tomcat5.5/bin/startup.sh jasperserver is running.
Just add JAVA_HOME=/your/java/path and JRE_HOME=/your/java/path in catalina.sh.

This is more about tomcat java setting or default ubuntu java setting. Can you help me?

---

### Post by bangeko on 2008-11-27
I found this:
[https://bugs.launchpad.net/ubuntu/+source/tomcat5.5/+bug/76567]("https://bugs.launchpad.net/ubuntu/+source/tomcat5.5/+bug/76567")

---

