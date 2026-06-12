---
title: "libgnucrypto-java-2.0.1 error in rebuilding"
date: 2007-01-03
forum: Repositories &amp; Backports
---

### Post by paulajulienne on 2007-01-03
Hi I am rebuilding the package libgnucrypto-java-2.0.1 in Kubuntu Dapper and it always comes out with this error:

Exception SaslException is not compatible with throws clause in SaslClient.getNegotiatedProperty(String)

See the output below:

> 

Exception SaslException is not compatible with throws clause in SaslClient.getNegotiatedProperty(String)
----------
2 problems (1 error, 1 warning)make[2]: *** [gnu/crypto/jce/GnuCrypto.class] Err                                                           or 255
make[2]: Leaving directory `/home/paula/libgnucrypto-java-2.0.1/source'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/paula/libgnucrypto-java-2.0.1'
make: *** [debian/stamp-makefile-build] Error 2


---

