---
title: "HowTo install Tomcat 6 &gt;= 6.0.32 on Ubuntu 10.04 LTS"
date: 2011-12-01
forum: Server Platforms
---

### Post by lviggiani on 2011-12-01
Hi Everybody,
I need to install JIRA application on Ubuntu Server 10.04 LTS and Tomcat 6.
Unfortunately, Ubuntu 10.04 repos contains Tomcat 6.0.24-2ubuntu1.9 which seems not suitable for JIRA as it contains a [[COLOR="blue"]critical bug[/COLOR]]("https://issues.apache.org/bugzilla/show_bug.cgi?id=48694") as stated [[COLOR="Blue"]here[/COLOR]]("http://confluence.atlassian.com/display/JIRA044/Installing+JIRA+on+Tomcat+6.0") (Before You Begin section - first bullet).
How can I install (or upgrade to) Tomcat 6 >= 6.0.32 on my server?
Thanks, Luca.

---

### Post by lviggiani on 2011-12-02
> **lviggiani said:**
> Hi Everybody,
I need to install JIRA application on Ubuntu Server 10.04 LTS and Tomcat 6.
Unfortunately, Ubuntu 10.04 repos contains Tomcat 6.0.24-2ubuntu1.9 which seems not suitable for JIRA as it contains a [[COLOR="blue"]critical bug[/COLOR]]("https://issues.apache.org/bugzilla/show_bug.cgi?id=48694") as stated [[COLOR="Blue"]here[/COLOR]]("http://confluence.atlassian.com/display/JIRA044/Installing+JIRA+on+Tomcat+6.0") (Before You Begin section - first bullet).
How can I install (or upgrade to) Tomcat 6 >= 6.0.32 on my server?
Thanks, Luca.

...ok I found the solution in the end... is here:
[http://www.botra.eu/2011/04/13/tomcat-6-su-ubuntu-10-04-lts/]("http://www.botra.eu/2011/04/13/tomcat-6-su-ubuntu-10-04-lts/")
It's in Italian but I think it should be easy to follow anyway.

---

