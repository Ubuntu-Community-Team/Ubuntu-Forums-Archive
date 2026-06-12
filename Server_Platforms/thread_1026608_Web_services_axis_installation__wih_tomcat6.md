---
title: "Web services:: axis installation  wih tomcat6"
date: 2008-12-31
forum: Server Platforms
---

### Post by anix1 on 2008-12-31
Hello,

**axis** install is not succeded with **tomcat6**. I have searched many times without solution found. I don't use Eclipse, I use only batch commands. I used this urls (but no solution where found) (some urls are in french):
[I][http://ubuntuforums.org/showthread.php?t=227286&highlight=axis+install](http://ubuntuforums.org/showthread.php?t=227286&highlight=axis+install)
[http://ws.apache.org/axis/java/install.html](http://ws.apache.org/axis/java/install.html)
[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu) [/I]

Tomcat6 is working well ([http://localhost:8080](http://localhost:8080) works without problems)
Here is the error returned when I put "http://localhost:8080/axis" in the browser:

---------------------------------------------------------------------------------------------
Status HTTP 404 - /axis

type: status report

message /axis

description The ressource is not available
Apache Tomcat/6.0.18
---------------------------------------------------------------------------------------------

> Here is my configuration :
[I]Server version: Apache/2.2.9 (Ubuntu)
Apache Tomcat Version 6.0.18
axis versions used: axis2-1.4.1 et axis1-4 (both does not work)
Ubuntu 8.10 (xubuntu gnome)[/I]


Thank you for your help !

---

### Post by anix1 on 2009-01-03
Thank you, it is resolved now. I missed the wright directory of tomcat.

---

### Post by kosumo on 2009-05-21
I got the same error as what you got. How did you resolve it?

---

### Post by anix1 on 2009-05-22
I forgot what I did; but I remember that I found the solution at final

---

