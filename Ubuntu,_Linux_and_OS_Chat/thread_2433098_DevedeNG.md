---
title: "DevedeNG"
date: 2019-12-13
forum: Ubuntu, Linux and OS Chat
---

### Post by amadness on 2019-12-13
Why is DevedeNG no longer in the repos? I had to download it from here: [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

### Post by yetimon_64 on 2019-12-13
> **amadness said:**
> Why is DevedeNG no longer in the repos? I had to download it from here: [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

```
yetiman:~ $  version
Description:    Ubuntu 18.04.3 LTS ...
```

I am on Ubuntu mate 18.04, which uses the standard Ubuntu repositories, and devede is available (just not named with the "NG" at the end). I don't have it installed here but it IS available in the repositories.

What Ubuntu version are you running?

```
yetiman:~ $  apt-cache policy devede
devede:
  Installed: (none)
  Candidate: 4.8.0-1
  Version table:
     4.8.0-1 500
        500 http://archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages
        500 http://archive.ubuntu.com/ubuntu bionic/multiverse i386 Packages
```

**Edit:** You may need to check you have the multiverse repo enabled in "Software Sources" or "Software and Updates" (the name will depend on what flavor and/or release of ubuntu you are using.)

---

