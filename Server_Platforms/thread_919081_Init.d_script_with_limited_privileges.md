---
title: "Init.d script with limited privileges"
date: 2008-09-13
forum: Server Platforms
---

### Post by Doomsword on 2008-09-13
Hi, I'd like to launch a init.d script as a simple user: how could I do that? My script at system startup is always executed as root user

Here's my script permission:

```
-rwxr--r-- 1 doom doom 251 2008-09-13 22:12 ./COD4_start.sh
```

and init.d task to my script:

```
-rwxr-xr-x 1 root root 399 2008-09-13 23:14 /etc/init.d/COD4
```

Thank you very much in advance,

Fabio

---

### Post by RealPSL on 2008-09-13
All init scripts are run by root by default. To run it as yourself I would recommend the following in your init script.

```
su - myuser -c "/path/to/script"
```

If you use that to call your program in the init script it will run as you.

---

