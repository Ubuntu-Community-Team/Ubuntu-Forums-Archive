---
title: "Noob installing OpenBD"
date: 2010-03-13
forum: Server Platforms
---

### Post by iamlex on 2010-03-13
For being a pretty noobish Linux user, I've done okay so far.  Got MySQL, Apache, Tomcat, and OpenBD all installed and running.

However, when I try to access [http://127.0.0.1:8080/openbd/bluedragon/administrator/](http://127.0.0.1:8080/openbd/bluedragon/administrator/) I get an exception: javax.servlet.ServletException: BlueDragon: Init Parameter BLUEDRAGON_WORKING_DIRECTORY Error: java.security.AccessControlException: access denied (java.io.FilePermission /var/lib/tomcat6/webapps/openbd/WEB-INF/bluedragon/work write)

I believe I need to change some directory permissions, but I can't determine exactly what.  ](*,)

TIA!

---

### Post by iamlex on 2010-03-15
Okay, so when I browsed to the path that was causing the error (/var/lib/tomcat6/webapps/openbd/WEB-INF/bluedragon/work), I quickly realized the problem...

It didn't exist!

/var/lib/tomcat6/webapps/openbd/WEB-INF/bluedragon$ sudo mkdir work
/var/lib/tomcat6/webapps/openbd/WEB-INF/bluedragon$ cd work
/var/lib/tomcat6/webapps/openbd/WEB-INF/bluedragon/work$ sudo mkdir temp

That did the trick.

---

