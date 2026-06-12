---
title: "Tomcat file permissions"
date: 2010-04-15
forum: Server Platforms
---

### Post by zeez on 2010-04-15
Hello lads,

I was attempting to deploy an application on tomcat6, and when i try to access it on my browser i get this error message

> 
Installing Configuration file
Unanticipated error: access denied (java.io.FilePermission /var/lib/tomcat6/webapps/aha2/WEB-INF/web.xml write)
This is NOT supposed to happen at all, possibly some JAVA library is not functioning as expected, check if you're realy using JDK 1.4.0 (or better)

System.getProperty("java.version")=1.6.0_0
Installation FAILEDConfiguration file is installed. If you wish to move AHA!, you have to edit web.xml afterwards.
Please restart the server. 


i gave 777 permissions to the file and it does not solve my problem.

Any ideas on how can i solve this

-------------------

I read somewhere i had to give change the owner of some directory to tomcat6 (user tomcat6), but i can no longer locate that site.

--------------------

i attempted to deploy the app this way 
> 
[http://localhost:8080/manager/deploy?path=/aha3&war=file:/media/kitty/andrew/aha/](http://localhost:8080/manager/deploy?path=/aha3&war=file:/media/kitty/andrew/aha/)


---

