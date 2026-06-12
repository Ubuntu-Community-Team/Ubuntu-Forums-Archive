---
title: "HAProxy help"
date: 2016-03-11
forum: Server Platforms
---

### Post by Marcos_Armas on 2016-03-11
Hi, I have a trouble with a system that consumes a WSDL service, this system receives a dataset and make a call to this webservice for each record of the datset, the problem is that is not using the keep-alive connection type neither is using threading, I can't modify the code of this system and I need to improve it, I think that HAProxy can help, It is possible to maintain a http-keep-alive connection type with the background requests and http-server-close with the front end? 

Please, anyone can propose something better?

---

