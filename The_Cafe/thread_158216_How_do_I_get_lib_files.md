---
title: "How do I get lib files"
date: 2006-04-10
forum: The Cafe
---

### Post by ishorseman on 2006-04-10
I am trying to install the real player plugin for firefox.
I downloaded RealPlayer10GOLD-1.bin.
set permissiond to make it executable.
When I execute :
 ./RealPlayer10GOLD-1.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I went to the application installer but can't find anything as simple as a library.

In the world of ubuntu how do I install this library.

---

### Post by gerbman on 2006-04-10
[QUOTE=ishorseman]I am trying to install the real player plugin for firefox.
I downloaded RealPlayer10GOLD-1.bin.
set permissiond to make it executable.
When I execute :
 ./RealPlayer10GOLD-1.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I went to the application installer but can't find anything as simple as a library.

In the world of ubuntu how do I install this library.[/QUOTE]From the terminal run```
sudo apt-get install libstdc++5
```

---

### Post by ishorseman on 2006-04-11
Thanks gerbman  that works slick.

---

### Post by gerbman on 2006-04-12
[QUOTE=ishorseman]Thanks gerbman  that works slick.[/QUOTE]Welcome :-D

---

