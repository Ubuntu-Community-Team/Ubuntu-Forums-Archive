---
title: "ddclient wont start"
date: 2007-02-13
forum: Server Platforms
---

### Post by creigscofield on 2007-02-13
I cant get ddclient to run on my server.  When I try to start the init.d script this is all I get;
```
creig@creigsroom:/etc/init.d$ sudo ./ddclient restart
 * dynamic DNS service update utility not in use 
   ...done.
creig@creigsroom:/etc/init.d$ sudo ./ddclient start
 * dynamic DNS service update utility not in use 
   ...done.
creig@creigsroom:/etc/init.d$ sudo ./ddclient force-reload
 * dynamic DNS service update utility not in use 
   ...done.
creig@creigsroom:/etc/init.d$ sudo ./ddclient stop
 * dynamic DNS service update utility not in use 
   ...done.
creig@creigsroom:/etc/init.d$ sudo ./ddclient start
 * dynamic DNS service update utility not in use 
   ...done.

```

---

