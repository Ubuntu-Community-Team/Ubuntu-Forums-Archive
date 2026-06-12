---
title: "howto connect? after install &quot;plone-site&quot; package"
date: 2008-03-06
forum: Server Platforms
---

### Post by adieb on 2008-03-06
Hey People.

I´ve just installed plone-site by using synaptic. It installed quite a lot packages like python and stuff like that.

Well, after that i tried to connect to it by typing: [http://localhost:8081](http://localhost:8081)
but firefox says it can´t establish the connection. The Port is the one i choose.

trying [http://localhost:8081/manage](http://localhost:8081/manage) is the same.

what can i do?

---

### Post by luisromangz on 2008-03-06
Check that you are running the zope server.

---

### Post by adieb on 2008-03-06
alright. but how? what kind of server is it? which command does it start?

"sudo /etc/init.d/zope2.10 (and zope2.9)  start"   says  "no instances found."

after creating an instance using "dzhandle" it started. But I still can´t connect to it through webbroweser


???

---

### Post by SkyyBugg on 2008-05-09
Grep the process table for zope.  If there is a process out there then 
try the url you had plus /Plone

If that doesn't work I recommend trying the Universal Installer from Plone.org.   It installs everything in your user directory.

---

