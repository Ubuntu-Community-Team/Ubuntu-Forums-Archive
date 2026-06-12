---
title: "cgi-bin location error"
date: 2011-06-28
forum: Server Platforms
---

### Post by gazz1982 on 2011-06-28
Dear forum,

I have an ubuntu server, all works great and has been for 2 years :-)However, I am now implementing openlayers, which also works fine except I need to point the openl;ayers script to the proxy.cgi file
```
OpenLayers.ProxyHost="proxy.cgi?url=";
```

The error I get returned is:

```
Not Found 

The requested URL /sgc_new/proxy.cgi was not found on this server. 
Apache/2.2.14 (Ubuntu) Server at www.singlegrave.nl Port 80 
```

the proxy.cgi file is in /usr/lib/cgi-bin/ but it is searching in the webroot folder, this is not an openlayers issue but an Apache issue.

Any help most appreciated.

Gary

---

