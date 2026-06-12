---
title: "[SOLVED] Windows Printer - requires python3-smbc which is NOT available; pkg added"
date: 2020-04-21
forum: Ubuntu Development Version
---

### Post by maestrobwh1 on 2020-04-21
When I go to attach to my network printer attached to a Win 10 machine, the printer manager barks that it needs to install extra software, and when clicked, it is not a package that exists in the 20.04 repos.  Python3-smbc [python3-smbc_1.0.15.6-2_amd64 is the latest in 19.10 and yes, I tried using gdebi to install it and it won't install obviously due to unsatisfied dependency issues).

---

### Post by Morbius1 on 2020-04-21
Did you enable "Universe" in Software & Updates? That is where python3-smbc is located.
[ATTACH=CONFIG]285575[/ATTACH]

---

### Post by maestrobwh1 on 2020-04-21
Yep, had that enabled.  How very strange.  I tried to add it up to today (several times) and no good.  Today, it is in the repos.  Thanks

---

