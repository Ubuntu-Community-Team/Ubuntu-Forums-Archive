---
title: "WebKitWebProcess crashed"
date: 2018-03-31
forum: Ubuntu Development Version
---

### Post by VMC on 2018-03-31
"WebKitWebProcess crashed with SIGSEGV in WTFCrash"

I've been getting this crash on each boot-up. There's several bug reports. All pointing to this one:
[https://bugs.launchpad.net/ubuntu/+source/webkit2gtk/+bug/1752108](https://bugs.launchpad.net/ubuntu/+source/webkit2gtk/+bug/1752108)

If your having the same issue, that's the one to report on.

---

### Post by jbicha on 2018-03-31
The only webkit2gtk crash I'm aware of is described in the recent Debian.NEWS entry for webkit2gtk
[https://anonscm.debian.org/git/pkg-webkit/webkit.git/tree/debian/NEWS](https://anonscm.debian.org/git/pkg-webkit/webkit.git/tree/debian/NEWS)

That affected deja-dup but that was fixed for Ubuntu 18.04 LTS two weeks ago.

---

### Post by VMC on 2018-04-06
It crashed again using the XFCE beta version, just installed.

---

### Post by VMC on 2018-04-13
What I now know is that the webkit crash is caused by 'google-chome' only. Both lubuntu and xubuntu crash using 'google-chrome', but not Firefox.

---

