---
title: "jboss jrockit Permission denied"
date: 2009-12-30
forum: Server Platforms
---

### Post by vra5107 on 2009-12-30
Hi

      I have installed jboss 4.2.3-GA on sun jvm. After encountering Permgen space exceptions, I decided to switch to jrockit. For this I edited the run.conf of jboss to add the following. 

JAVA="/home/venkat/jrmc-3.1.2-1.6.0/jre/bin"

But I get the following error when I try to start the server.

/usr/local/share/jboss-4.2.3.GA/bin/run.sh: 255: /home/venkat/jrmc-3.1.2-1.6.0/jre/bin: Permission denied

I am convinced I am not doing something right with JVM configuration. Could somebody help me.

Thanks
venkat

---

