---
title: "Scalix install"
date: 2008-06-16
forum: Server Platforms
---

### Post by sunstriker on 2008-06-16
because i couldn't get calendar server to compile. I took a shot at installing Scalix, which is more that just caldav, I know. But I still want to try it. 
I followed a guide i've found ([http://www.suares.an/index.php?page_id=1&news_id=211#news-top](http://www.suares.an/index.php?page_id=1&news_id=211#news-top))
At some point it gave an error that it couldn't find /etc/opt/scalix-tomcat/scalix-tomcat.conf. I tried to create the file itself (empty) so the installer could continue. The installer completed succesfully but I get a huuuuuge Java stacktrace coming from Tomcat. restarting scalix-tomcat via the init script gives the following error: ```
Instance (mainframe) is not running
Starting Tomcat service (mainframe)The JAVA_HOME environment variable is not defined
This environment variable is needed to run this program

```
Although this variable is set in /etc/profile. I think it has something to do with the scalix-tomcat.conf. Anyone has an example of the file or some solution?

---

