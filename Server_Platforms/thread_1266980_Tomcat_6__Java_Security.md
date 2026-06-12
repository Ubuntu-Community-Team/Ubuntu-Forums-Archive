---
title: "Tomcat 6 / Java Security"
date: 2009-09-15
forum: Server Platforms
---

### Post by HolyFlirkingShnit on 2009-09-15
Hi everyone,
 
I have installed Tomcat 6 and the Sun JDK 6 and both seem to be working well (so far). I have managed to deploy successfully (for the large part) a web application to Tomcat 6 and it works for the most part - but there is one thing I cannot figure out and maybe someone can point me in the right direction..
 
The Web app is Mondrian, and the test application that ships with it works fine except for one thing (whether or not I use the test app or my own data behind it). I am trying to work with the XMLA provider which is simply a 'service' provided by the mondrian application. This work perfectly on a windows box but I am receiving a security error message (a connection refused message from java security on the java.net namespace). Tomcat security is disabled completely.
 
Besides the tomcat security settings, is there anywhere else that can be causing a problem like this? It does not seem to make any sense...
 
Cheers
 
HFS

---

### Post by tomcatProb on 2009-09-20
Hi, Can u pls help me by mentioning the steps to deploy a website on Tomcat 6. My site is working correctly and shows every page on Windows XP, but not working on Ubuntu. In both XP and Ubuntu i am using tomcat 6, MySql. All variables JAVA_HOME, CATALINA_HOME etc are set, i have my java class files in the WEB_INF/class/projectName folder. But when i login through my JSP page control is not going to the java files(servlets), and java null pointer exception is shown.

---

