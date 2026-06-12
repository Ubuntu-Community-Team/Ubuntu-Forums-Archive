---
title: "why does the system not recognize &quot;service mysql status&quot; without sudo?"
date: 2015-02-18
forum: Server Platforms
---

### Post by stupidquestion on 2015-02-18
If I go "service mysql status" I get:
status: Unknown job: mysql

But if I go "sudo service mysql status", I get the expected behavior:
mysql start/running, process 1295

Can anyone please explain this behavior?

---

### Post by darkod on 2015-02-19
For protection and security the standard root user is sort of "disabled" in ubuntu. The first user created during install has sudo rights to execute system commands and has full control but only when sudo is appended in front of the command you want to run.

Depending on the command sometimes it will work without sudo and sometimes not. Because in this case you want to check the status of a service, you need sudo to get the info from the system.

---

### Post by MAFoElffen on 2015-02-22
+1 

(additional) Some commands, such as 
```

service <serviceName> <state> 

```
can only be run with root previledges, therefore... Darkod's explaination.

---

