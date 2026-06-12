---
title: "tomcat6 package in 9.04 is broken"
date: 2009-06-19
forum: Server Platforms
---

### Post by zcox on 2009-06-19
On a fresh install of Ubuntu 9.04 (using Alestic AMI ami-0d729464) on Amazon EC2, the tomcat6 package appears to install broken.  I do:

apt-get install tomcat6

then put our .war file in /var/lib/tomcat6/webapps, do a

/etc/init.d/tomcat6 restart

and then see this in /var/log/syslog:

Jun 19, 2009 3:30:46 PM org.apache.catalina.users.MemoryUserDatabase save WARNING: User database is not persistable - no write permissions on directory

That is followed by numerous other errors saying Tomcat can't start properly.  Tomcat then always shows the 404 Not Found page when trying to access the site from a browser.

I've fixed this in the past by setting TOMCAT6_SECURITY=yes in /etc/default/tomcat6 but that just seems like a bad hack.

Does anyone know which directory Tomcat is complaining about not having write permissions?

Thanks,
Zach

---

### Post by zcox on 2009-06-19
Update: so I did

chown -R tomcat6:tomcat6 /etc/tomcat6

and now I don't see the write privileges error, but now I see this in /var/log/syslog:

Jun 19 16:18:20 ip-10-251-90-10 jsvc.exec[5460]: Java HotSpot(TM) Client VM warning: Can't detect initial thread stack location - find_vma failed 
Jun 19 16:18:22 ip-10-251-90-10 jsvc.exec[5460]: Jun 19, 2009 4:18:22 PM org.apache.coyote.http11.Http11Protocol init INFO: Initializing Coyote HTTP/1.1 on http-80 
Jun 19 16:18:22 ip-10-251-90-10 jsvc.exec[5460]: Jun 19, 2009 4:18:22 PM org.apache.catalina.startup.Catalina load INFO: Initialization processed in 1119 ms 
Jun 19 16:18:22 ip-10-251-90-10 jsvc.exec[5460]: Jun 19, 2009 4:18:22 PM org.apache.catalina.core.StandardService start INFO: Starting service Catalina 
Jun 19 16:18:22 ip-10-251-90-10 jsvc.exec[5460]: Jun 19, 2009 4:18:22 PM org.apache.catalina.core.StandardEngine start INFO: Starting Servlet Engine: Apache Tomcat/6.0.18 
Jun 19 16:18:24 ip-10-251-90-10 jsvc.exec[5460]: Jun 19, 2009 4:18:24 PM org.apache.catalina.core.StandardContext start SEVERE: Error listenerStart 
Jun 19 16:18:24 ip-10-251-90-10 jsvc.exec[5460]: Jun 19, 2009 4:18:24 PM org.apache.catalina.core.StandardContext start SEVERE: Context [] startup failed due to previous errors 
Jun 19 16:18:24 ip-10-251-90-10 jsvc.exec[5460]: Jun 19, 2009 4:18:24 PM org.apache.catalina.startup.HostConfig deployWAR INFO: Deploying web application archive adcondor.war 
Jun 19 16:18:25 ip-10-251-90-10 jsvc.exec[5460]: Jun 19, 2009 4:18:25 PM org.apache.catalina.core.StandardContext start SEVERE: Error listenerStart 
Jun 19 16:18:25 ip-10-251-90-10 jsvc.exec[5460]: Jun 19, 2009 4:18:25 PM org.apache.catalina.core.StandardContext start SEVERE: Context [/adcondor] startup failed due to previous errors 
Jun 19 16:18:25 ip-10-251-90-10 jsvc.exec[5460]: Jun 19, 2009 4:18:25 PM org.apache.coyote.http11.Http11Protocol start INFO: Starting Coyote HTTP/1.1 on http-80 
Jun 19 16:18:25 ip-10-251-90-10 jsvc.exec[5460]: Jun 19, 2009 4:18:25 PM org.apache.catalina.startup.Catalina start INFO: Server startup in 3394 ms


Still getting the 404 response from Tomcat when trying to load the site in a browser.  I'm guessing the problems start with the "Can't detect initial thread stack location" error.  Does anyone know what that even means or how to fix it?

---

### Post by rdlugosz on 2009-07-14
I was having a similar strange problem.  I had one of my webapps complaining about not being able to read a xerces.properties file (which it seemed to expect within the JRE directory...).  

Anyway, no idea why it was doing this; setting the TOMCAT6_SECURITY to no fixed the issue.  That said, any time you set a security option to "no" it can't be a great solution... would love to hear further thoughts on this one.

---

### Post by randallecook on 2009-07-15
I installed tomcat 6 with Synaptic, and started it with 'sudo ./startup.sh' issued in the /usr/share/tomcat6/bin directory. It fired up OK (well, after I created a logs directory as a sibling of bin), but I can't seem to shut it down. When I run the shutdown.sh script in the same directory, I get a java.io.FileNotFoundException: /usr/share/tomcat6/conf/server.xml (No such file or directory). I think this is because the tomcat files are split between /usr/share/tomcat6 (executables) and /var/lib/tomcat6 (configuration and data). Reading the tomcat 6 documentation, I get the feeling that tomcat expects to live under a single roof so to speak. So, yes, broken in 9.04. BTW, I noticed the same /usr/share vs. /var/lib division with glassfish

---

### Post by randallecook on 2009-07-20
To paraphrase *The Matrix*, it is not tomcat that is broken, it is only myself.

My mistake was using the /usr/share/tomcat6/bin/startup.sh script to launch tomcat. I should have used the init.d mechanism, which sets up and splits CATALINE_HOME and CATALINA_BASE correctly. I discovered this when I started up up my computer today after leaving it off since my last post, and found tomcat running, and running properly.

I found it hard to believe that the Ubuntu folks would break so popular a package as tomcat, and in fact they did not. They probably should put a README in /usr/share/tomcat6 and/or /var/lib/tomcat6, however.

---

