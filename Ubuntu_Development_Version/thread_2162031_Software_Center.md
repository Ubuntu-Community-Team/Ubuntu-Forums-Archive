---
title: "Software Center"
date: 2013-07-12
forum: Ubuntu Development Version
---

### Post by synaptix on 2013-07-12
Anyone else having problems with it? Mine suddenly won't startup and this is the output from terminal:

```
2013-07-12 19:38:06,891 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 429, in __init__
    self.useful_cache = UsefulnessCache(True)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 91, in __init__
    self._retrieve_votes_from_server()
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 105, in _retrieve_votes_from_server
    user = get_person_from_config()
  File "/usr/share/software-center/softwarecenter/utils.py", line 638, in get_person_from_config
    cfg = get_config()
  File "/usr/share/software-center/softwarecenter/config.py", line 180, in get_config
    _software_center_config = SoftwareCenterConfig(filename)
  File "/usr/share/software-center/softwarecenter/config.py", line 38, in __init__
    super(SoftwareCenterConfig, self).__init__()
TypeError: must be type, not classobj
```

---

### Post by ping-wu on 2013-07-12
Had the same problem.  Most recent update solved the problem. 

(Please change your Title to [solved].  Thanks.)

---

### Post by synaptix on 2013-07-12
> **ping-wu said:**
> Had the same problem.  Most recent update solved the problem. 

(Please change your Title to [solved].  Thanks.)

Actually the most recent update broke mine, lol.

---

### Post by Elfy on 2013-07-13
Updated - got the same issue *if* I try and use it.

---

### Post by OrangeCrate on 2013-07-13
> **Elfy said:**
> Updated - got the same issue **"if"** I try and use it.

:)

---

### Post by mc4man on 2013-07-13
likely
[lpbug]1198822[/lpbug]

see this on a live session, on a 2 week old install opens ok

---

### Post by synaptix on 2013-07-13
> **mc4man said:**
> likely
[lpbug]1198822[/lpbug]

see this on a live session, on a 2 week old install opens ok

That's it. Clean install of Alpha 1, software center worked. After first round of updates, it still worked. Then I got some more updates later that evening and then it stopped working. :/

---

### Post by mc4man on 2013-07-13
Figured out what the issue is here, maybe not the ultimate fix but certainly should resolve S-c segfaulting

```
sudo apt-get install python-configparser
```

Edit: I see that there is a new S-c in proposed that  fixs  this - so scratch the above & install s-c 13.07-0ubuntu1

---

### Post by synaptix on 2013-07-13
> **mc4man said:**
> Edit: I see that there is a new S-c in proposed that  fixs  this - so scratch the above & install s-c 13.07-0ubuntu1

Cool. I'll just wait until it hits updates. Using proposed in the past has borked my installs.

---

### Post by ping-wu on 2013-07-13
You're right.  I ran S-c again, and now it's broken, again, with the same message as you posted.:mad:

---

