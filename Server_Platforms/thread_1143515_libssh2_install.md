---
title: "libssh2 install"
date: 2009-04-30
forum: Server Platforms
---

### Post by m3bik on 2009-04-30
I'm trying to install libssh2 on my ubuntu server.

When I run ./configure I get this error message:
> checking for OpenSSL... configure: error: Cannot find OpenSSL's <evp.h> or <hma.h>


I've ran:
```
apt-get install openssl
```

Everything appeared to install successfully, but I still get the same error message...

---

### Post by m3bik on 2009-04-30
Do I maybe need to download the actual openssl source files instead of simply installing through apt-get?

---

### Post by m3bik on 2009-04-30
I couldn't find openssl-dev anywhere. I installed libssl-dev and it appears to be working fine now...

---

