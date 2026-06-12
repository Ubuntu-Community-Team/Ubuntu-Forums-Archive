---
title: "tomcat manager doesn't work"
date: 2010-07-31
forum: Server Platforms
---

### Post by edortizq on 2010-07-31
Hi experts, I'm really new with Ubuntu and have the following problem:

I installed successfully sun-java6-jdk using
apt-get install sun-java6-jdk

Then set up the JAVA_HOME environment variable to "/usr/lib/jvm/java-6-sun-1.6.0.20"

And then installed successfully tomcat6 using
apt-get install tomcat6
apt-get install tomcat6-admin tomcat6-examples tomcat6-docs

Everything seem to be right, when I try the browser with
[http://localhost:8080](http://localhost:8080) return a webpage with "It works !" and other text

But, if I try [http://localhost:8080/manager/html](http://localhost:8080/manager/html) then returns 404 error, the error is something like "The required resource (manager/html) is not available" (that is my translation from the spanish text "[U]El recurso requerido (/manager/html) no está disponible")

[/U]The same happens when I try 
[http://localhost:8080/docs/](http://localhost:8080/docs/)  or
[http://localhost:8080/examples/](http://localhost:8080/examples/) or
[http://localhost:8080/host-manager/html](http://localhost:8080/host-manager/html)

Please your help!!

---

### Post by Reason NL on 2010-12-03
You should install these parts separately:

Manager: sudo apt-get install tomcat6-admin
Docs: sudo apt-get install tomcat6-docs
Examples: sudo apt-get install tomcat6-examples

---

