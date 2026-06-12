---
title: "keylogger ?"
date: 2009-04-02
forum: Security
---

### Post by tsq on 2009-04-02
are keyloggers possible in linux, ie program sets keyboard hook and tries to catch what user types into non own/child window ?

any way to prevent it ?

---

### Post by canadiandude007 on 2009-04-02
With Linux unlike Windows it is a lot more difficult for programs to be installed without you doing so yourself, especially in Ubuntu since you would need elevated status (sudo or gksudo) to do so.  The only real danger would be from rootkits or other such malware being installed unknowingly by yourself.

Otherwise it is a lot less likely you will need to worry about key loggers.

---

### Post by bodhi.zazen on 2009-04-02
> **tsq said:**
> are keyloggers possible in linux, ie program sets keyboard hook and tries to catch what user types into non own/child window ?

any way to prevent it ?

Yes it is possible, one needs root access and, usually X access.

Take a look at : [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

I just updated that thread yesterday :)

and also X security.

[http://www.x.org/wiki/Development/Documentation/Security](http://www.x.org/wiki/Development/Documentation/Security)

In general we do not support installing key loggers (it is a slippery slope) and unless you are cracked you are OK, thus the link to Ubuntu Security.

---

