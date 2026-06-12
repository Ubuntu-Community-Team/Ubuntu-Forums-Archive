---
title: "Delete/remove last two lines &amp; `uname -r`"
date: 2010-01-15
forum: The Cafe
---

### Post by 5ive on 2010-01-15
I've created code that will delete the last two lines:
```
dpkg-l linux-image-*-generic | sed 'N;$!P;$!D;$d'
```
and that will erase the result of `uname-r`:
```
dpkg-l linux-image-*-generic | sed'/'$( uname-r) '/ d'
```
I checked and it works. Just do not know how to combine these two codes into one that you first remove the last two lines, then delete what will the result of `uname-r`. If it turns out that the list of `dpkg-l` there is no kernel showed the result of what `uname-r` then nothing will do.
Can anyone help and sorry for English, but I'm still weak?

---

### Post by Xbehave on 2010-01-15
Whitespace matters in bash so your commands are
```
dpkg -l linux-image-*-generic | sed 'N;$!P;$!D;$d' 
```
```
dpkg -l linux-image-*-generic | sed /$( uname -r )/d
```
to combine just use ";" (it's not clever but it works)
so it would work as
```
dpkg -l linux-image-*-generic | sed 'N;$!P;$!D;$d' ; dpkg -l linux-image-*-generic | sed /$( uname -r )/d
```
but i don't see the point in the first command

---

### Post by 5ive on 2010-01-15
```
dpkg -l linux-image-*-generic | sed '/^ii/!d;N;$!P;$!D;$d'
```
```
dpkg -l linux-image-*-generic | sed '/^ii/!d;/$(uname -r)/d'
```



```
dpkg -l linux-image-*-generic | sed '/^ii/!d;N;$!P;$!D;$d;/$(uname -r)/d'
```
Does not work

---

### Post by Xbehave on 2010-01-16
Im not sure what your tying, did you try my ugly fix?
reading your description you could try and do it using head
```
dpkg -l linux-image-*-generic | head -n -2 | sed /$( uname -r )/d
```

---

