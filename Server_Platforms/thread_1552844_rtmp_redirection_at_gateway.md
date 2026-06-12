---
title: "rtmp redirection at gateway"
date: 2010-08-14
forum: Server Platforms
---

### Post by jamesbon on 2010-08-14
Is it possible to re direct the requests coming at gateway from internet
in following format

rtmp://[site1.mydomain.com]("http://site1.mydomain.com/")
rtmp://[site2.mydomain.com]("http://site2.mydomain.com/")
rtmp://[site3.mydomain.com]("http://site3.mydomain.com/")
rtmp://[site4.mydomain.com]("http://site4.mydomain.com/")

by squid to internal servers which are actually hosting [site1.mydomain.com]("http://site1.mydomain.com/")
[site2.mydomain.com]("http://site2.mydomain.com/") or things like this.
This is not a load balancing thing all of them are different server
with different contents.
If not by squid then is there some other way ?

---

