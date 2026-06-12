---
title: "Apache2 and Tomcat6 working together"
date: 2011-03-09
forum: Server Platforms
---

### Post by Clean1414 on 2011-03-09
I would like detailed information on how to get Tomcat6 and Apache2 to seamlessly work together. I know how to deploy an application into Tomcat and make it Available via [www.domainname.com:8080/mainapp](www.domainname.com:8080/mainapp) but what i would like to do is set an application that tomcat can read to root but also make it so i can use phpmyadmin if i so choose. to clarify. [www.thisdomain.com](www.thisdomain.com) would take you to the main application that tomcat would read but [www.thisdomain.com/phpmyadmin](www.thisdomain.com/phpmyadmin) would take you to phpmyadmin like always and apache would process said request. any help is greatly appreciated. I forgot to mention that I am using Ubuntu Server  10.10 x86.

---

### Post by wongo888 on 2011-03-09
Sample mod_proxy setup:

[http://confluence.atlassian.com/display/JIRA/Integrating+JIRA+with+Apache](http://confluence.atlassian.com/display/JIRA/Integrating+JIRA+with+Apache)

---

