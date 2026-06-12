---
title: "Mcafee install in ubuntu 10.10"
date: 2010-12-21
forum: Security
---

### Post by deepucha on 2010-12-21
hey guys today i was trying to install mcafee enterprise ed on my ubuntu10.10
got the following error msg

```
dpkg: error processing MFErt.i686.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 MFErt.i686.deb
```

i tried to copy the contents of mounted folder to another and retried same error msg followed
i used furious iso mount 

i was trying to install runtime environment first as per the instrucions in installation guide
:popcorn:
attaching screenshots plz help....

---

### Post by cariboo on 2010-12-21
Try:

```
sudo dpkg -i ./MFErt.i686.deb
```

---

