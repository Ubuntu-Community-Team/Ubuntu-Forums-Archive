---
title: "Warning message while installning tomcat6"
date: 2009-05-27
forum: Server Platforms
---

### Post by oakdeveloper on 2009-05-27
Hi,

I have installed tomcat6 on my Ubuntu 9.04 machine today. I used the tomcat which I downloaded from the Apache Tomcat web site. During the installation process, I received a warning message which I have highlighted in red in the snapshot below. Please shed some light on what the message implies and how I could avert this warning.

```
oakdeveloper@oakbook:/opt/tomcat$ sudo nano /etc/init.d/tomcat
[sudo] password for oakdeveloper: 
oakdeveloper@oakbook:/opt/tomcat$ sudo chmod 755 /etc/init.d/tomcat
oakdeveloper@oakbook:/opt/tomcat$ sudo update-rc.d tomcat defaults
[COLOR=Red]update-rc.d: warning: /etc/init.d/tomcat missing LSB information[/COLOR]
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/tomcat ...
   /etc/rc0.d/K20tomcat -> ../init.d/tomcat
   /etc/rc1.d/K20tomcat -> ../init.d/tomcat
   /etc/rc6.d/K20tomcat -> ../init.d/tomcat
   /etc/rc2.d/S20tomcat -> ../init.d/tomcat
   /etc/rc3.d/S20tomcat -> ../init.d/tomcat
   /etc/rc4.d/S20tomcat -> ../init.d/tomcat
   /etc/rc5.d/S20tomcat -> ../init.d/tomcat
oakdeveloper@oakbook:/opt/tomcat$ 
```Thanks,
Babu

---

### Post by Waappu on 2009-06-21
Hi

It is only warning. If Tomcat works and starts ok you do not need worry about that

---

