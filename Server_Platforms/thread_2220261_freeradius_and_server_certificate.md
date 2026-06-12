---
title: "freeradius and server certificate"
date: 2014-04-27
forum: Server Platforms
---

### Post by conormclaughlin on 2014-04-27
Hello,

I have set up freeradius + mysql + CA + server certificate on ubuntu.

1. Users CAN log in with username/password and CA certificate installed on device; (good)
2. Users CANNOT log in with username/password and a wrong certificate installed on device; (good)

Problem:

3. Users CAN log in with username/password and no CA certificate installed.

Does anyone know why this might be? I don't understand why the supplicant device is not at least bringing up a warning about the certificate if freeradius has been configured to use a server certificate?

Thanks in advance,
cmcl

---

