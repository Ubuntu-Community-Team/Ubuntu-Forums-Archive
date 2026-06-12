---
title: "[SOLVED] TomCat Application installation problem"
date: 2007-10-26
forum: Server Platforms
---

### Post by borobudur on 2007-10-26
I have installed tomcat and it seems to work properly. 
I can install and list an application with ant successfully. But if I try to start it I get this:
```
FAIL - Application at context path /spring could not be started
```If I have a look in the application server directory, it's empty:
```
/var/cache/tomcat5/Catalina/localhost/spring/
```In this dir I have a server:
```
/var/cache/tomcat5/Catalina/localhost/jsp-examples/tldCache.ser
```
I check to log-files: nothing!

I think it could be an permission problem but I wasn't successful with changing the mod to 777

Any idea?
borobudur

---

### Post by borobudur on 2007-11-04
The problem was this property was wrong:
```
appserver.home=/usr/share/tomcat5
```in [I]build.properties

[/I]

---

