---
title: "problem with make menuconfig"
date: 2012-08-01
forum: Server Platforms
---

### Post by nikibg on 2012-08-01
I must compile one linux distribution .
When i try menuconfig its return me 
```
root@ubuntuserver1:~/10mm50-90/linux-2.6.24.7# make menuconfig
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:0:
scripts/kconfig/lxdialog/dialog.h:32:20: fatal error: curses.h: No such file or directory
compilation terminated.
make[1]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make: *** [menuconfig] Error 2
```
Why that happend :confused:

---

### Post by rubylaser on 2012-08-01
You need to grab the curses library as the error message mentions.  This should do it.

```
sudo apt-get install libncurses5-dev libncursesw5-dev
```

* Package names may be incorrect, I don't have access to 12.04 box at this point to check the repos.

---

### Post by nikibg on 2012-08-02
10x it is working :)

---

