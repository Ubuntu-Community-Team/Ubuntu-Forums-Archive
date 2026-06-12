---
title: "Is Focal Fossa past the point of including Python 3.8.0 (Oct 14 release)?"
date: 2019-10-25
forum: Ubuntu Development Version
---

### Post by Skaperen on 2019-10-25
Is Focal Fossa past the point of including Python 3.8.0 (Oct 14 release)?

---

### Post by cruzer001 on 2019-10-25
It's not part of the default install

---

### Post by PaulW2U on 2019-10-25
But it's in the repositories:   :)
```
paul@C50B:~$ apt policy python3.8
python3.8:
  Installed: (none)
  Candidate: 3.8.0-2
  Version table:
     3.8.0-2 500
        500 http://gb.archive.ubuntu.com/ubuntu focal/main amd64 Packages
```

---

### Post by harry332 on 2019-10-26
There is a transition from python3.7 to 3.8 going on at the moment.
Still a lot of packages hasn't been build against it yet, some like gedit, libpeas, python-uno and so on.
When they have, the meta package python3 will be updated.

---

### Post by Skaperen on 2019-10-28
so, does that mean the final release of Focal Fossa in April 2020 will include Python 3.8?

---

### Post by harry332 on 2019-10-28
Very likely Ubuntu Focal Fossa 20.04 will have Python 3.8 as default.
You can read more of the plans from Phoronix:
[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Focal-Open-Development](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Focal-Open-Development)

---

