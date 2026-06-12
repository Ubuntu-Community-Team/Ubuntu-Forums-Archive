---
title: "Problem with squid and transparent mode"
date: 2009-07-13
forum: Server Platforms
---

### Post by waltervalderrama on 2009-07-13
Hello everybody, i need some help with squid. I have a Proxy-LAN topology:
 
                               Internet
                                  |
                                  |
                                Proxy
                                  |
                                  |
                                Switch
                               /  |   \
                              /   |    \
                             /    A     \
                         Server         B

Proxy is configured for PCs A and B in transparent mode, but when I want to acces to Server from A, packets first go to the Proxy and after that go to the Server. Result a "not authorized" message. 

I cannot change Server settings because it is not under my administration, so I have to find a way for A or B to access to Server without going to proxy.

Any ideas?

---

### Post by jpeddicord on 2009-07-13
Moved to Server Platforms. Tutorials & Tips is not a support forum. Thanks! :)

Jacob

---

