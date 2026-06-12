---
title: "update-rc.d problem"
date: 2010-02-18
forum: Server Platforms
---

### Post by simonbowen on 2010-02-18
Hi, I am trying to get a start up script to work, i have a file /etc/init.d/blah (with 755 permissions) with the contents [http://pastebin.com/m4131b7c6](http://pastebin.com/m4131b7c6). I have run "update-rc.d -f blah defaults". But when I reboot the script is not executing, can one of you help me out?

---

### Post by Albert Net on 2010-02-26
What is the output after you issue

```
update-rc.d -f blah defaults
```

?

---

