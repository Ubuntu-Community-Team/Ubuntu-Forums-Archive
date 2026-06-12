---
title: "/bin/sh damaged !"
date: 2011-08-20
forum: Server Platforms
---

### Post by hnumanoglu on 2011-08-20
Hi friends, I wrongly made a brilliant action and overwrite one test script on to /bin/sh file. Now my scripts are not working and I m very doubtful about restarting machine. How can I fix /bin/sh file. I checked from another ubuntu and it seems unreadable...??
 
Any ides or experiences?
 
Thanks,

---

### Post by ~!geek!~ on 2011-08-20
Overwrite the /bin/sh using live cd

---

### Post by hnumanoglu on 2011-08-20
thanks for the reply, I copied /bin/bash to /bin/sh and seems working correctly.. I ll update if I find something wrong...
 
Thanks,

---

### Post by sisco311 on 2011-08-20
> **hnumanoglu said:**
> thanks for the reply, I copied /bin/bash to /bin/sh and seems working correctly.. I ll update if I find something wrong...
 
Thanks,

In Ubuntu, /bin/sh is a symlink to /bin/dash, so if /bin/dash is intact then you should remove /bin/sh and recreate it as a symlink to dash.

---

### Post by fdrake on 2011-08-20
> **hnumanoglu said:**
> thanks for the reply, I copied /bin/bash to /bin/sh and seems working correctly.. I ll update if I find something wrong...
 
Thanks,

well bash is a little bit different than sh.

why don't you just do ```
sudo apt-get install dash
```

---

### Post by fdrake on 2011-08-20
> **sisco311 said:**
> In Ubuntu, /bin/sh is a symlink to /bin/dash, so if /bin/dash is intact then you should remove /bin/sh and recreate it as a symlink to dash.

well if /bin/sh is a symbolic link to /bin/dash. doesn't that mean he changed dash too by changing sh?   well unless he just over wrote the whole file.

---

### Post by sisco311 on 2011-08-20
> **fdrake said:**
> well bash is a little bit different than sh.

why don't you just do ```
sudo apt-get **--reinstall** install dash
```

Fixed your command. ;)

Just tested it on my chroot environment, and yes, reinstalling dash should do the trick:
```
sisco@acme:~/xtmp$ ll /bin/sh
-rwxr-xr-x 1 root root 950896 2011-08-20 22:32 /bin/sh*
sisco@acme:~/xtmp$ sudo apt-get install --reinstall dash
sisco@acme:~/xtmp$ ll /bin/sh
lrwxrwxrwx 1 root root 4 2011-05-03 18:04 /bin/sh -> dash*

```

---

