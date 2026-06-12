---
title: "Cruisecontrol installation"
date: 2009-03-30
forum: Server Platforms
---

### Post by jubajuba on 2009-03-30
I downloaded the binary cruisecontrol 2.8.2 distribution from [http://cruisecontrol.sourceforge.net/download.html](http://cruisecontrol.sourceforge.net/download.html) .
According to the install documentation I should unzip the file, make the cruisecontrol.sh and apache-ant-1.7.0/bin/ant executable and then run cruisecontrol.sh
Cruisecontrol seems  to run, but the webserver and other management interfaces does not.
I get the following error when i run cruisecontrol.sh:
```
java.lang.NoClassDefFoundError: mx4j.log.Log4JLogger
   at java.lang.Class.initializeClass(libgcj.so.90)
   at net.sourceforge.cruisecontrol.jmx.CruiseControlControllerAgent.<init>(CruiseControlControllerAgent.java:95)
   at net.sourceforge.cruisecontrol.Main.startJmxAgent(Main.java:147)
   at net.sourceforge.cruisecontrol.Main.start(Main.java:128)
   at net.sourceforge.cruisecontrol.launch.Launcher.run(Launcher.java:259)
   at net.sourceforge.cruisecontrol.launch.Launcher.main(Launcher.java:117)
Caused by: java.lang.NullPointerException
   at java.lang.Class.initializeClass(libgcj.so.90)
   ...5 more
```
I've checked that mx4j and log4j is included in the classpath...
The log files only tell me that cruisecontrol tries to build the default project. 
Anyone run in to something similar?

---

### Post by HDave on 2009-08-17
Did you ever solve this?

---

### Post by periphery on 2011-03-17
Having the same issue with 2.8.4, the cruise control documentation seems pretty poor at best. It makes the assumption that  things will just work.

---

### Post by jubajuba on 2011-03-17
Hi,
I solved this problem (or just ignored it), I know we were able to get Cruisecontrol to work. But since it's been two years and since I had this problem at a previous employer (I no longer have access to the server) I can't remember or find out what I did... I'm sorry. Hope someone else can shed light on things if it's still a problem.

---

