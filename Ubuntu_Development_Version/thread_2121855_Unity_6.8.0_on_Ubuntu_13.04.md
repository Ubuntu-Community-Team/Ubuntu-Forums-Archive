---
title: "Unity 6.8.0 on Ubuntu 13.04"
date: 2013-03-03
forum: Ubuntu Development Version
---

### Post by ezcomputersolutions on 2013-03-03
Hey guys!

Why is Ubuntu 13.04 still using Unity 6.6.0 when Ubuntu 12.10 has Unity 6.8.0?(Or some other version) I created a USB with a persistent space on it. Installed all of the Ubuntu 13.04 updates, and it was still on Unity 6.6.0. Since Unity 6.8.0 was released all the way back in October it seems like we should have the latest Unity version. Anybody know why?

To check the version of unity that I have I typed this into my terminal:
```
unity --version
```

---

### Post by screaminj3sus on 2013-03-03
synaptic says the unity verson for raring is "6.12.0daily13.03.01-0ubuntu1", I think its reporting the wrong version with that command or something, maybe a bug?

---

### Post by Cheesemill on 2013-03-03
Are you sure your system is fully updated?

13.04 is currently on Unity version 6.12.0.

[http://packages.ubuntu.com/search?keywords=unity&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=unity&searchon=names&exact=1&suite=all&section=all)

---

### Post by Cheesemill on 2013-03-03
It's a bug, I have the same results as you...

```
root@raring:~# apt-cache policy unity
unity:
  Installed: 6.12.0daily13.03.01-0ubuntu1
  Candidate: 6.12.0daily13.03.01-0ubuntu1
  Version table:
 *** 6.12.0daily13.03.01-0ubuntu1 0
        500 http://uk.archive.ubuntu.com/ubuntu/ raring/main amd64 Packages
        100 /var/lib/dpkg/status
root@raring:~# 
root@raring:~# 
root@raring:~# unity --version
unity 6.6.0
```

---

### Post by ezcomputersolutions on 2013-03-03
Ok, great. Thanks guys :)

---

### Post by mc4man on 2013-03-03
Maybe a bug, maybe just doesn't matter & no one changes it in CMakeLists.txt for each minor release
#
# Base bits
#
set (PROJECT_NAME "unity")
set (UNITY_MAJOR 6)
set (UNITY_MINOR 6)
set (UNITY_MICRO 0)
set (UNITY_VERSION "${UNITY_MAJOR}.${UNITY_MINOR}.${UNITY_MICRO}")
set (UNITY_API_VERSION "6.0")

---

