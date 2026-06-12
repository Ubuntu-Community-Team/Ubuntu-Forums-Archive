---
title: "apt-get install tomcat5.5 does not set $CATALINA_HOME, help needed."
date: 2009-01-14
forum: Server Platforms
---

### Post by tnek on 2009-01-14
I installed Tomcat 5.5 on Ubunty Hardy using "apt-get install tomcat5.5 tomcat5.5-admin". The server seem to be running and I get a blank page on port 8180. However, CATALINA_HOME isn't set.

I've found nothing to help me out here. How should I set CATALINA_HOME? And are there other things I need to do?

I'm also wondering about what user and password I should specify for localhost:8080/admin to get into the admin web application (provided by the tomcat5.5-admin package).

Any and all help would be highly appreciated!

---

### Post by tnek on 2009-01-16
I edited /env/environment and added CATALINA_HOME=/var/lib/tomcat5.5 , was that the way to do it?

I'm also wondering, during apt-get install tomcat5.5 the user tomcat55 was added to the system. Does such users have passwords? And if so, how can I find out what it is?

---

