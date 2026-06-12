---
title: "Openswan troubles generating new host key"
date: 2010-03-29
forum: Server Platforms
---

### Post by atlet on 2010-03-29
I have Ubuntu Server 8.04 LTS 64bit, virtualizet with XEN.
When I run  ```
ipsec newhostkey --output /etc/ipsec.secrets
``` it doesn't happen nothing, it get stuck there. 

I searched the google but I didn't find any solutions for now. 

Any idea what I can do or what is wrong?

---

### Post by atlet on 2010-03-29
Workaround
```
mv /dev/random /dev/chaos
ln -s /dev/urandom /dev/random
```

---

