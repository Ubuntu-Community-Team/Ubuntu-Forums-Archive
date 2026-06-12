---
title: "Wine installed, but can use &quot;wine&quot; from terminal"
date: 2009-01-18
forum: Wine
---

### Post by Nexusx6 on 2009-01-18
Hi all, I got a weird problem after I installed wine from apt-get. Though it is indeed installed as I can run the games I had installed from a previous version of wine, I can't call it from command line. 
```
$ wine
bash: /usr/local/bin/wine: No such file or directory
```

Previously I had compiled and patched wine from source, but when it turned out I no longer needed those patches in the newer versions I used "make uninstall" to remove the old version and got the new one from apt-get. I'm sure some where along this path the /bin files for wine disappeared, but I don't know where to or how to restore them.

I'm running Kubuntu 8.04

---

### Post by taurus on 2009-01-18
The one you installed with apt-get should be in /usr/bin.

```
whereis wine
```

---

### Post by Nexusx6 on 2009-01-19
Awesome, thanks for the reply. The bin files were indeed under /usr/bin/ so I copy/pasted them under /usr/local/bin/ to get wine working. No idea why it's looking under local, but everything is working now.

---

