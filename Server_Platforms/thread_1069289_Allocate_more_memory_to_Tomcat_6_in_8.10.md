---
title: "Allocate more memory to Tomcat 6 in 8.10?"
date: 2009-02-13
forum: Server Platforms
---

### Post by madde001 on 2009-02-13
I just installed Ubuntu 8.10 and the Tomcat 6 setup is unfamiliar to me, with Tomcat server now starting as a system process.

If I need to allocate more Java heap to my Tomcat, where do I change that setting?

---

### Post by o_sam_o on 2009-05-27
just edit the /ect/init.d/tomcat6 file, change the JAVA_OPTS

e.g. change it to:
JAVA_OPTS="-Djava.awt.headless=true -Xmx512M -XX:MaxPermSize=256m"

---

### Post by JeppeM on 2009-05-27
Note that if you're using the 32 bit version of ubuntu, you can't assign more than a few GB to tomcat... We had to strap our installation and install the 64bit since our tomcat needs 10 GB :)

It's actually not the OS bit version, but the java bit version from what i remember, so make sure you have 64 bit java as well if you want more memory... :)

---

### Post by al_mic on 2012-09-07
On newer ubuntu versions you must edit /etc/default/tomcat6 
The JAVA_OPTS from that file will be the one setting the memory.

---

### Post by nothingspecial on 2012-09-07
Old thread, closed.

---

