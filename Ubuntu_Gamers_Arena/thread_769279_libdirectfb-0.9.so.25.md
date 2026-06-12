---
title: "libdirectfb-0.9.so.25"
date: 2008-04-26
forum: Ubuntu Gamers Arena
---

### Post by wililupy on 2008-04-26
Hello

I just upgraded from 7.10 to 8.04 and now, UT2004 doesn't work with the following error:

wililupy@desktop:/usr/local/games/UT2004/System$ sudo ./ut2004-bin
[sudo] password for wililupy: 
./ut2004-bin: error while loading shared libraries: libdirectfb-0.9.so.25: cannot open shared object file: No such file or directory
wililupy@desktop:/usr/local/games/UT2004/System$

I have looked everywhere for this library, and I can't find a single package that carries this library. 

Any help would be greatly appreciated.

---

### Post by Perfect Storm on 2008-04-27
Try with:
```
sudo ln -s /usr/lib/libdirectfb-1.0.so.0 /usr/lib/libdirectfb-0.9.so.25
```

---

