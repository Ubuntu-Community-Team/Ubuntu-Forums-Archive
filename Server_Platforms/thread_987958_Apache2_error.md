---
title: "Apache2 error"
date: 2008-11-20
forum: Server Platforms
---

### Post by dragos240 on 2008-11-20
Hey guys, i was wondering, my apache won't start, i'm not running the ubuntu server edition for this, but i figured since it's "server related" i should post here, i got the following error.
```

apache2: symbol lookup error: apache2: undefined symbol: apr_os_uuid_get

```I think the problem was i tried to install apache by downloading the unix source first and failed then. Then i used sudo apt-get install apache2. It's really annoying and it wont start and it's just failing :(.
Can anyone suggest a fix?

---

### Post by threetimes on 2008-11-20
Remove anything left from your source installation, and try again.
If that won't work, reinstall apache after removing your souce installation.

---

