---
title: "proxy_ajp with different urls"
date: 2009-04-16
forum: Server Platforms
---

### Post by rogier.de.groot on 2009-04-16
How do you connect Tomcat and Apache so that the URL on Apache is different from the one in Tomcat? For example, I have two servers running tomcat with one apache frontend. Both have the manager app installed. I'd like to map them as /server1/manager and /server2/manager on one of my apache virtual hosts.
I tried using something like the following but it didn't work:

<Location /server1/manager>
  ProxyPass ajp://server1:8009/manager
  ProxyPassReverse ajp://server1:8009/manager
</Location>

---

### Post by rogier.de.groot on 2009-04-20
Anyone? I find it hard to believe that I'm the only one who wants to do something like this...

---

