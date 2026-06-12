---
title: "[SOLVED] Installing CUPS Windows drivers"
date: 2008-06-03
forum: Server Platforms
---

### Post by LRT on 2008-06-03
i have a fresh install of ubuntu 8.04 server and i am trying to install the CUPS windows drivers (cups-windows-6.0-source.tar.gz)

i already installed cupsys (`apt-get install cupsys`)

i then downloaded cups-windows-6.0-source.tar.gz and unpacked and entered the directory

when i ran `make install` i got the error:

make: command not found

so then i ran `apt-get install make` and then ran `make install` again and got this error:

/bin/sh: cups-config: not found


anyone know what is going on??

---

### Post by beniwtv on 2008-06-03
You are missing the cups-config utility. 

You can obtain it by installing the libcupsys2-dev package.

```
sudo apt-get install libcupsys2-dev
```

Cheers,

---

### Post by LRT on 2008-06-03
that was it! thanks!!

---

### Post by beniwtv on 2008-06-03
Glad we could help. Don't forget to mark your thread as solved if it is. :popcorn:

---

