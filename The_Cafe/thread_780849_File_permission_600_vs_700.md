---
title: "File permission 600 vs 700?"
date: 2008-05-03
forum: The Cafe
---

### Post by Thieflock on 2008-05-03
I am just curious what the difference is between a 777 and 666 for example. Is it that 777 are for executable files and 666 is for text files?

---

### Post by capink on 2008-05-03
octal permissions work like this:

if you want read permission you add 4. so a permission of 444 allows the files to be read only.

if you want write permission you add 2. so a permission of 666 allows the files to be read and written.

if you want execute permission you add 1. so a permission of 777 allows the files to be read and written as well as executed.

why there are three permission?
the first number indicate the premission granted for the owner of the file.

the second number indicate the premission granted for the users blonging to the group of the file.

the third number indicate the premissions granted for the rest of the users.

---

### Post by Dr Small on 2008-05-03
```

Owner - Group - Other
 rwx  -  rwx  -  rwx (700)
 rw   -  rw   -  rw  (666)
 rwx  -       -      (700)
 rwx  -  r x  -  r x (755)

R = Read
W = Write
X = eXecute
```

---

### Post by herbster on 2008-05-04
This should explain it quite well: [http://dmiessler.com/study/unixlinux_permissions/](http://dmiessler.com/study/unixlinux_permissions/)

---

