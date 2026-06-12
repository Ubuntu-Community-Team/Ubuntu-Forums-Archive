---
title: "SSL with a NON-SSL Program ... SSL Proxy"
date: 2007-06-02
forum: Server Platforms
---

### Post by scott_ttocs46 on 2007-06-02
Hi all,

      I am a n00b to ssl. So, bare with me. I have a server application that broadcasts on a certain port that does not have ssl capability. However, all of the client applications have ssl capability. Is there some way I can tunnel, proxy, or do something so that I can send and receive communication via ssl? 

Regards,
Scott

---

### Post by EmmEff on 2007-06-02
[Stunnel](http://www.stunnel.org/)

---

### Post by BhRaviKiran on 2008-04-16
HI,
     Plz answer this too. The application running on Ubuntu is activated with SSL. The client application on Windows PC is equipped with SSL. When the client communicates with the server then i get SSL error.

"error:00000000::lib(0):func(0):reason(0)".

Does this mean SSL is not enabled on Ubuntu? 

The /usr/lib folders are updated with the latest SNMP libraries and were compiled with openssl.

The application on ubuntu should receive the request from Windows client.

Thanks and Regards,
Ravi.

---

