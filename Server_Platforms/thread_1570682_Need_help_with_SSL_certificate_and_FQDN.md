---
title: "Need help with SSL certificate and FQDN"
date: 2010-09-08
forum: Server Platforms
---

### Post by thegaffney on 2010-09-08
Hello, 

I got a certificate installed with the CN as midfifty.com

but im always getting this in my error log when apache restart

```
[warn] RSA server certificate CommonName (CN) `midfifty.com' does NOT match server name!?

```my servers internal FQDN is apache-server.midfifty.local

should i re-do the certificate to make the CN that name even though its my internal domain?

or should the CN just be apache-server?

the ssl certificate is also a multi domain certificate that midfifty.com and classic-haulers.com shares if that makes a difference


Thanks !

---

