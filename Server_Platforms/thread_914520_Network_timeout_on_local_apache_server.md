---
title: "Network timeout on local apache server"
date: 2008-09-08
forum: Server Platforms
---

### Post by allspiritseve on 2008-09-08
I have apache2 installed on my laptop. As of yesterday, I can't browse my local server through firefox. I get a "Network timeout, the server is taking too long to respond". Apache2 is still running, and reloading doesn't do anything. Anyone have any ideas on what I can do?

---

### Post by allspiritseve on 2008-09-09
This is pretty much the contents on my apache error.log file:

```
[Tue Sep 09 03:09:10 2008] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Tue Sep 09 03:09:10 2008] [notice] caught SIGWINCH, shutting down gracefully
```

It happens every time I restart the server.

---

### Post by allspiritseve on 2008-09-09
Ok, well, I found a fix:

[http://ubuntuforums.org/showthread.php?p=4187042#post4187042](http://ubuntuforums.org/showthread.php?p=4187042#post4187042)

---

