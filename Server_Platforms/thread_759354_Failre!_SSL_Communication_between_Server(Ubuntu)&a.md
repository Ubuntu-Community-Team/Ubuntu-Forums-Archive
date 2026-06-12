---
title: "Failre! SSL Communication between Server(Ubuntu)&amp;Client(Windows)"
date: 2008-04-19
forum: Server Platforms
---

### Post by BhRaviKiran on 2008-04-19
Hi,
    We have a Mono winform (version 1.2.4) application (server) running in Ubuntu 7.10 box. There is another application running on Windows XP box (client) . The two PCs are accessible to each other in the network.  We have installed the OpenSSL version 0.9.8e on Ubuntu box. 
  
The applications in the two operating systems are supposed to communicate with each other. The application in the XP box has the SSL enabled and should communicate with the Ubuntu application where SSL is already enabled. 
 
When the client communicates with the server then we get the popup window titled "SSL Error" with description  "error:00000000::lib(0):func(0):reason(0).
 
We have also checked the "/etc/mono/config" configuration settings.
The symbolic links libssl.so and libcrypt.so are present as entries of dllmap and referring to the targets libssl.so.0.9.8 and libcrypt-2.6.1.so respectively. These libraries are already present in the /usr/lib directories. 
 
As a test whether SSL is enabled on the Ubuntu, we have tried the following command :
**openssl s_server -accept 50002.**
 
The client application was able to communicate with Ubuntu console at the particular port. The Ubuntu root console is able to receive the request from the client. So SSL is enabled at Ubuntu PC.
 
So why the mono winform application in the Ubuntu is unable to receive the client request when the SSL is turned on at either sides?
 
Thanks in advance.
Bh. Ravi Kiran

---

### Post by HermanAB on 2008-04-19
[http://www.google.ca/search?q=error%3A00000000%3A%3Alib(0)%3Afunc(0)%3Areason(0)&ie=utf-8&oe=utf-8&aq=t&rls=com.mandriva:en-US:official&client=firefox-a](http://www.google.ca/search?q=error%3A00000000%3A%3Alib(0)%3Afunc(0)%3Areason(0)&ie=utf-8&oe=utf-8&aq=t&rls=com.mandriva:en-US:official&client=firefox-a)

---

