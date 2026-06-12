---
title: "eclipse drop-down menu in toolbar not working in ubuntu 14.04  trusty"
date: 2014-02-23
forum: Ubuntu Development Version
---

### Post by hoboy on 2014-02-23
I have strugled with this issues for long long time I hope to get some assistance here.
Since I have upgrade to "Distributor ID:	Ubuntu
Description:	Ubuntu Trusty Tahr (development branch)
Release:	14.04
Codename:	trusty
"
eclipse drop-down menu in toolbar stop to work

---

### Post by Satya_Swaroop_DAMA on 2014-02-23
Hi ... I had the same issue... I solved it by adding the line "export UBUNTU_MENUPROXY=0" at the end of *.profile *file... I restarted it later but I don't know if this is even needed.... Also please refer to [http://askubuntu.com/questions/361040/eclipse-menus-are-cut-off-or-dont-show#363237](http://askubuntu.com/questions/361040/eclipse-menus-are-cut-off-or-dont-show#363237) for more details... ENJOY!

---

### Post by hoboy on 2014-02-25
Satya_Swaroop_DAMA
Thanks very very much I have struggled with this problem all too long
tks it is solved with your suggestion.

---

### Post by roudy1989 on 2014-03-03
Anyone knows if this will get fixed in the global menu? As I found some bug reports they stated that global menu does not behave right.

---

