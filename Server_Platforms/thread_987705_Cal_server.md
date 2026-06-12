---
title: "Cal server"
date: 2008-11-19
forum: Server Platforms
---

### Post by vidgpersonrsw on 2008-11-19
We (me and the main server admin) are trying to use Calendar Server (calendarserver.org). But the UI is HORRENDOUS the documentation is practically nonexistent, and we can't find where the files are stored. Please help us!

---

### Post by y@w on 2008-11-19
Haha by horrendous documentation you mean no documentation? This software is really early in the development stage.. Does it just store them as an .ics file? It *looks* like from the documentation that it installs everything into the subdirectory that you download it to. If both are correct, you could always do something like this in the directory you downloaded it to (or root for that matter if you wanted to wait that long..) :

```
sudo find . | grep ics
```

If you still can't find it, post the contents of conf/caldavd-dev.plist from the calendarserver directory. That might tell us the storage directory..

---

