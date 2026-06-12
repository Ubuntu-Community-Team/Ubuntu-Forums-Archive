---
title: "ImportError: No module named testlib"
date: 2012-10-05
forum: Security
---

### Post by Stonecold1995 on 2012-10-05
I'm trying to run [test-kernel-security.py]("http://bazaar.launchpad.net/~ubuntu-bugcontrol/qa-regression-testing/master/view/head:/scripts/test-kernel-security.py") from [this Ubuntu wiki page]("https://wiki.ubuntu.com/Security/Features"), but when I try to run it I get the following error:

```
alex@kubuntu:~$ python test-kernel-security.py
Traceback (most recent call last):
  File "test-kernel-security.py", line 49, in <module>
    import testlib
ImportError: No module named testlib
```

How do I add this module?

---

### Post by Stonecold1995 on 2012-10-20
bump

---

### Post by zombifier25 on 2012-10-20
I think you also need to download [this file](https://bazaar.launchpad.net/~ubuntu-bugcontrol/qa-regression-testing/master/view/head:/scripts/testlib.py) and put it in the same directory.

---

