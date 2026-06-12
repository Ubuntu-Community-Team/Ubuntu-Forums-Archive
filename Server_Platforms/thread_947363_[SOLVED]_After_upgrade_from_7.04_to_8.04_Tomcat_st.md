---
title: "[SOLVED] After upgrade from 7.04 to 8.04 Tomcat stopped loading web application"
date: 2008-10-14
forum: Server Platforms
---

### Post by ripos on 2008-10-14
I use Tomcat 5.5 on Ubuntu server edition. I used jdk5.
I have updated from 7.04 to 8.04 (not sure, 2.6.24-19-generic).
As far as I understand jdk was updated to jdk6.
After that one web application stopped working.

```
user@server:~$ sudo /etc/init.d/tomcat5.5 restart
 * Stopping Tomcat servlet engine tomcat5.5
   ...done.
 * Starting Tomcat servlet engine tomcat5.5
   ...done.

```

After that in catalina log file (with stacktraces stripped):

```
Oct 14, 2008 3:00:45 PM org.apache.coyote.http11.Http11BaseProtocol pause
INFO: Pausing Coyote HTTP/1.1 on http-8180
Oct 14, 2008 3:00:46 PM org.apache.catalina.core.StandardService stop
INFO: Stopping service Catalina
Oct 14, 2008 3:00:46 PM org.apache.coyote.http11.Http11BaseProtocol destroy
INFO: Stopping Coyote HTTP/1.1 on http-8180
Oct 14, 2008 3:00:46 PM org.apache.catalina.core.AprLifecycleListener lifecycleEvent
INFO: Failed shutdown of Apache Portable Runtime

Oct 14, 2008 3:00:54 PM org.apache.catalina.core.AprLifecycleListener lifecycleEvent
Oct 14, 2008 3:00:54 PM org.apache.coyote.http11.Http11BaseProtocol init
INFO: Initializing Coyote HTTP/1.1 on http-8180
Oct 14, 2008 3:00:54 PM org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 810 ms
Oct 14, 2008 3:00:54 PM org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
Oct 14, 2008 3:00:54 PM org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/5.5
Oct 14, 2008 3:00:54 PM org.apache.catalina.core.StandardHost start
INFO: XML validation disabled
Oct 14, 2008 3:00:54 PM org.apache.catalina.startup.HostConfig deployDescriptor
[b]SEVERE: Error deploying configuration descriptor ROOT.xml
org.apache.commons.logging.LogConfigurationException: User-specified log class 'org.apache.commons.logging.impl.Log4JLogger' cannot be found or is not useable.[/b]
Oct 14, 2008 3:00:55 PM org.apache.catalina.core.StandardContext preDeregister
SEVERE: error stopping 
org.apache.commons.logging.LogConfigurationException: User-specified log class 'org.apache.commons.logging.impl.Log4JLogger' cannot be found or is not useable.
Oct 14, 2008 3:00:55 PM org.apache.catalina.startup.HostConfig deployDirectory
SEVERE: Error deploying web application directory ROOT
org.apache.commons.logging.LogConfigurationException: User-specified log class 'org.apache.commons.logging.impl.Log4JLogger' cannot be found or is not useable.
Oct 14, 2008 3:00:55 PM org.apache.coyote.http11.Http11BaseProtocol start
INFO: Starting Coyote HTTP/1.1 on http-8180
Oct 14, 2008 3:00:55 PM org.apache.catalina.storeconfig.StoreLoader load
Oct 14, 2008 3:00:55 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 1245 ms

```

Server is starting up fine, but one of web applications (ROOT) is not loaded.
It was working before update. It is working on my other servers under Mac OS.
I have no way to check it on 7.04 again, there is only one Ubuntu server in my installation.

I have tried to apt-get remove and apt-get install tomcat.

I'm googling for two days now. I'm stuck.
I will appreciate any help.

---

### Post by lykwydchykyn on 2008-10-14
Have you tried removing java 6 and installing java 5?  It's in the repos.  

You also might check that liblog4j1.2-java is installed, it seems that it's having trouble locating that library.

---

### Post by ripos on 2008-10-14
Lib, that you suggested was already installed. Using jdk5 does not change anything.
As far as I understand from googling the cause of this error is related to versions of libraries, classloader and class loading order. There is no working solution on the internet.

Freshly installed Tomcat [http://blog.datajelly.com/company/blog/54-installing-apache-tomcat-6-on-ubuntu.html](http://blog.datajelly.com/company/blog/54-installing-apache-tomcat-6-on-ubuntu.html) is working much better.
I have some troubles configuring it right, but application at least runs.

*sigh* There was so much pain in default Tomcat in Ubuntu 7.04, looks like it comes again.

---

### Post by ripos on 2008-10-15
After a lot of tries I give up. 
apt-get remove tomcat5.5.
No /etc/default, no /var/lib, no /usr/share, no links, no complex user rights.
I could not manage to make it work any other way.

So let it be, manually unpacked Tomcat runned under root using init.d script in less then half a kilobyte.

---

