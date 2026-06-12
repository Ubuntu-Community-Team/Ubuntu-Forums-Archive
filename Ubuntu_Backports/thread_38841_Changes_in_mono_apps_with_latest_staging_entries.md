---
title: "Changes in mono apps with latest staging entries"
date: 2005-06-02
forum: Ubuntu Backports
---

### Post by infinito on 2005-06-02
With latest entries about Mono in staging, there have been some changes in related apps:

- F-spot now works perfectly

- Beagle 0.10 doesn't work. Don't know exactly why. Reverting to 0.0.9 just works as usual.

The packages updated where:
```
beagle_0.0.10-0ubuntu1~5.04ubp1_i386.deb
gtk-sharp-gapi_1.0.10-0ubuntu1~5.04ubp1_i386.deb
libgconf-cil_1.0.10-0ubuntu1~5.04ubp1_all.deb
libglade-cil_1.0.10-0ubuntu1~5.04ubp1_i386.deb
libglib-cil_1.0.10-0ubuntu1~5.04ubp1_i386.deb
libgnome-cil_1.0.10-0ubuntu1~5.04ubp1_i386.deb
libgtk-cil_1.0.10-0ubuntu1~5.04ubp1_i386.deb
```

---

### Post by Slo Mo Snail on 2005-06-02
Hm, what doesn't work for you with the new beagle? It seems to work for me unless I have overseen some feature ;)

---

### Post by jdong on 2005-06-02
Beagle 0.10 actually works better than the previous release.

The old GTKsharp was actually broken

---

### Post by infinito on 2005-06-02
[QUOTE=jdong]Beagle 0.10 actually works better than the previous release.

The old GTKsharp was actually broken[/QUOTE]
 Ok, now it works, but i have to do a little weird thing....
```
$ rm -fr ~/.beagle
$ sudo apt-get remove --purge beagle
$ sudo apt-get install beagle
```
Everything seems ok. I've noticed that contacts search now works! Great!

---

