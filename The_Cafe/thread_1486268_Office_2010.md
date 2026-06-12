---
title: "Office 2010"
date: 2010-05-17
forum: The Cafe
---

### Post by sandyd on 2010-05-17
Does anyone know where the office 2010 downloaded MSIs are hidden?

Ive checked C:\windows\temp
and C:\windows\installers
already

---

### Post by Tibuda on 2010-05-17
Have you tried to search *.msi files in c:\ using Windows search engine?

---

### Post by sandyd on 2010-05-17
> **danielrmt said:**
> Have you tried to search *.msi files in c:\ using Windows search engine?
yup.

---

### Post by new_tolinux on 2010-05-17
Have you tried to open the command prompt and then do:
```
cd\
dir -a *.msi /s
```
The windows search engine isn't that good.

the -a option is to display all files (including system/hidden files) and the /s is for recursive mode.

---

### Post by sandyd on 2010-05-17
does anyone know ANY of the office 2010 product (MSI) codes?
I just found a  hundred or so folders, and I don't feel like testing them.

---

### Post by kernelhaxor on 2010-05-17
I think Office uses a Setup.exe instead of a .msi

---

