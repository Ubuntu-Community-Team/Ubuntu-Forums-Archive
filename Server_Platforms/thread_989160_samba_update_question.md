---
title: "samba update question"
date: 2008-11-21
forum: Server Platforms
---

### Post by fouadk on 2008-11-21
hi everyone...

i have an 8.04 with samba....how do i upgrade samba to the latest version(3.2.4) without building from source, is there is any deb package ready made ???

thanks in advance

---

### Post by cdenley on 2008-11-21
> **fouadk said:**
> hi everyone...

i have an 8.04 with samba....how do i upgrade samba to the latest version(3.2.4) without building from source, is there is any deb package ready made ???

thanks in advance

Why do you want version 3.2.4? Even Ubuntu 8.10 only has 3.2.3. Recently released software doesn't make it to ubuntu until it has been tested. If you want untested software, install ubuntu 9.04.

---

### Post by fouadk on 2008-11-21
ok that should be fine...but i have a server with 8.04 and i am not thinking of upgrading to 8.10, is there is any way of getting samba in .deb ???

---

### Post by cdenley on 2008-11-21
> **fouadk said:**
> ok that should be fine...but i have a server with 8.04 and i am not thinking of upgrading to 8.10, is there is any way of getting samba in .deb ???
A .deb package for 3.2.4 that has dependencies met in 8.04, probably not.

---

### Post by fouadk on 2008-11-21
so its either compile from source or upgrade to 8.10, ill go with upgradin....

have you got any idea if samba 3.2.3 can be joined to windows server 2008 using 
```
net ads join -U Administrator
```

---

