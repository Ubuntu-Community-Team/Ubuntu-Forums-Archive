---
title: "Admin help! I changed my administrative privileges and didn't make another user..."
date: 2009-09-30
forum: Security
---

### Post by tsnow24 on 2009-09-30
I didn't want my user name to have admin privileges because I'm running a proxy filter (dansguardian) and I don't want to be able to uninstall it.

But I forgot to create another user name for my wife that would have admin privileges so that I could still do things like install programs etc. 

So now I'm up a creek.  I don't know what to do.  It won't even let me open the "Users and Groups" admin tool.

Help please!

---

### Post by bodhi.zazen on 2009-09-30
Boot to recovery mode and restore your privileges.

You can also set privileges with any live CD.

```
usermod -G admin -a <user>
```

where "<user>" is the user needing root access.

Then either exit and continue boot process or reboot.

---

### Post by tsnow24 on 2009-09-30
Awesome thanks!

---

