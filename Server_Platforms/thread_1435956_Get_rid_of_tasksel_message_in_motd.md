---
title: "Get rid of tasksel message in motd"
date: 2010-03-22
forum: Server Platforms
---

### Post by Znupi on 2010-03-22
Whenever I login to my EC2 server instance, I get this message:
```
---------------------------------------------------------------------
At the moment, only the core of the system is installed. To tune the 
system to your needs, you can choose to install one or more          
predefined collections of software by running the following          
command:                                                             
                                                                     
   sudo tasksel --section server                                     
---------------------------------------------------------------------
```
However, I've done all my installing needs through apt-get, so I want to get rid of that message. How can I do that? I know it's not a big problem, but it bugs me especially because I couldn't yet find a way to make it go away.

---

### Post by ksclarke on 2010-05-06
bump

---

### Post by ksclarke on 2010-05-06
okay, can answer my own bump

remove /etc/update-motd.d/51_update-motd to get rid of that annoying message

---

