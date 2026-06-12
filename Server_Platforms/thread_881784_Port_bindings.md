---
title: "Port bindings"
date: 2008-08-06
forum: Server Platforms
---

### Post by matthewboh on 2008-08-06
I'm trying to get Alfresco 2.9B up and running on an Ubuntu 8.04 server, but I keep running into an error about port 50500.  

Alfresco runs under tomcat, so I've stopped tomcat to see if there's something on 50500 outside of tomcat and when I run```
netstat -an | grep 50500
tcp6       0      0 :::50500                :::*                    LISTEN
```
How do I figure out what's binding to that port?  How do I change it?  I've done a search that says mediatomb uses it and is installed with 8.04, but when I run aptitude search, it says that it's not installed.

Any ideas?

---

### Post by cdenley on 2008-08-06
```

sudo lsof -i :50500 -n

```

---

