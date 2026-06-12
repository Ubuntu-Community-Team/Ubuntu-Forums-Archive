---
title: "Does /usr/lib/libgdk-3.so.0 has exactly correct link? :("
date: 2012-03-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tista on 2012-03-23
Guys,

I've experienced some ugly "Package building" error on my PP...

Although we have libgtk-3-0 ver. 3.3.20-0ubuntu1, I wonder this release might have some misdirections causing libgdk-3...

In fact, today "debuild" gave me a error on the step " dh_shlibdeps". So I've removed this symlink and re-link from 
```
/usr/lib/x86_64-linux-gnu/libgdk-3.so.0.320.0
```
to 
```
/usr/lib/libgdk-3.so.0
```
Then debuild goes well! ;)

It would cause something like library dependency information error for everything to be linked to libgdk... Anybody could confirm it? IMHO, It might be the bug on Multi-arch or so...

Cheers,
Tista.

---

### Post by Gregory Lee on 2012-03-23
I have no "/usr/lib/libgdk-3.so.0", only:
```
~$ ls -l /usr/lib/x86_64-linux-gnu/libgdk-3*
lrwxrwxrwx 1 root root     19 Mar 20 08:56 /usr/lib/x86_64-linux-gnu/libgdk-3.so.0 -> libgdk-3.so.0.320.0
-rw-r--r-- 1 root root 559784 Mar 20 08:57 /usr/lib/x86_64-linux-gnu/libgdk-3.so.0.320.0
```

---

