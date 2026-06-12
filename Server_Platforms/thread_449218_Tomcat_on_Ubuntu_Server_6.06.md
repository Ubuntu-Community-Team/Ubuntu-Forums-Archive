---
title: "Tomcat on Ubuntu Server 6.06"
date: 2007-05-20
forum: Server Platforms
---

### Post by btrichardson on 2007-05-20
Hello all,

I installed Tomcat5 on my Ubuntu Server 6.06 machine using apt-get.  I then set JAVA_HOME in /etc/default/tomcat5 and in /etc/environment to my Sun Java 6 install directory.  I also set CATALINA_HOME in /etc/environment to my top level Tomcat5 install directory, /usr/share/tomcat5.

Because I'm running Ubuntu Server without a GUI, I can't test the Tomcat server via localhost.  When I test it from another machine on my network via port 8005, nothing comes up.  I noticed in my server.xml file that a default virtual host is set up for localhost... is this causing my problems?  If so, what should I use for the host name in the virtual host configuration?

Thanks in advance!

---

### Post by mbradlcu on 2007-05-22
does 'netstat -upant' show the port listening?
maybe try using 'lynx' to connect locally, it wold be ugly but it would at least rule out network problems.

---

