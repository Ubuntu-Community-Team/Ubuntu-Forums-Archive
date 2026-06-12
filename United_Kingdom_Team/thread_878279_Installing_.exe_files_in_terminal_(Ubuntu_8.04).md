---
title: "Installing .exe files in terminal (Ubuntu 8.04)"
date: 2008-08-02
forum: United Kingdom Team
---

### Post by Gael33 on 2008-08-02
I've downloaded a .exe file onto my desktop ... how do I install the program using Terminal?

Gael.

---

### Post by GreenN00b on 2008-08-02
You need to install wine first. Then type
```
wine installer.exe
```

---

### Post by olgasmi on 2011-07-22
xxx@xxxlaptop:~$ wine installer.exe
err:winedevice:Servicemain driver L"FileDisk" failed to load. wine: Could not load L"C:\\windows\\system32\\installer.exe":module not found.

??

---

### Post by macroshaft on 2011-10-29
> **olgasmi said:**
> xxx@xxxlaptop:~$ wine installer.exe
err:winedevice:Servicemain driver L"FileDisk" failed to load. wine: Could not load L"C:\\windows\\system32\\installer.exe":module not found.

??

sudo apt-get install wine

wine installer.exe

where installer.exe is the name of the program you are trying to install.

---

