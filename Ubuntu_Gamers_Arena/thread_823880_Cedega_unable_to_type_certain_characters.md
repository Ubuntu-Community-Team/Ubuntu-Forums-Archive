---
title: "Cedega: unable to type certain characters"
date: 2008-06-09
forum: Ubuntu Gamers Arena
---

### Post by Vermind on 2008-06-09
Hello,
I am running a 64-bit Ubuntu on a Finnish UTF-8 locale, and noticed that I cannot type the letter m in any Cedega game. In the Cedega interface I can.
I am also unable to type scandinavian chars in cedega games. Typing while playing the same games with Wine works though (I have a 64-bit version of Wine).
However, if I run cedega with: ```
LC_ALL=C LD_LIBRARY_PATH=/lib32:/usr/lib32 cedega
``` I can type scandinavian chars åäö, but trying to type m results in the scandinavian ö.

Also, in (the 32-bit version of) Neverwinter Nights, a native Linux program, I am unable to type scandinavian chars unless I run it with ```
LD_LIBRARY_PATH=/lib32:/usr/lib32 nwn
```.
So, I am asking if there's a fix for typing m in Cedega games, I kind of like that letter sometimes. Furthermore, it seems broken that I have to override the LD_LIBRARY_PATH for 32-bit programs in order to use my locale.

System details: 
Ubuntu 8.04, kernel 2.6.24-19-generic (x86_64), locale:
```
LANG=en_GB.UTF-8
LC_CTYPE=fi_FI.UTF-8
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=
```


Help anyone?

---

