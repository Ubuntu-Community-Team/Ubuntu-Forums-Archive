---
title: "remove temporay files in Windows 7 but keep passwords"
date: 2014-01-27
forum: Windows
---

### Post by aspergerian on 2014-01-27
How do I retain passwords while removing temp files on Windows 7 computer?

---

### Post by cariboo on 2014-01-27
This has nothing to do with Ubuntu, moved.

---

### Post by Habitual on 2014-01-27
start > run > cmd
```
cd %tmp%
del *.*
cd %temp%
del *.*
exit
```

---

### Post by aspergerian on 2014-01-30
Habitual,

Thank you.

---

### Post by Habitual on 2014-01-30
You're very welcome.
It should be noted those are ***your*** temp and tmp variable directories.
Those commands only clean out ***your*****s***,  *not the system's which may be in c:\temp
or other users on the system who's locations are coded similar to yours, but only if they are logged in.
An Admin can find and clean those as well.

---

