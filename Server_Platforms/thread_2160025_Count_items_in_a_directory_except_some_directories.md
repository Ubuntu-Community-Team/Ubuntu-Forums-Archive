---
title: "Count items in a directory except some directories"
date: 2013-07-05
forum: Server Platforms
---

### Post by alfirdaous on 2013-07-05
Hello everybody

I am on a directory that contains files and folders, I would like to count item on that directory except some sub-directories:

+ www
++ folder1
++ folder2
++ folder3
++ folder4

I would like to count all items in www except folder 2 and 3

Thx in advance

---

### Post by sandyd on 2013-07-05
use something like
```

find . \( -iname "*" ! -iname "folder2" ! -iname "folder3" \)
```

---

### Post by steeldriver on 2013-07-05
I would use a 'path prune' I think

```
find www \( -path 'www/folder2' -o -path 'www/folder3' \) -prune -o -type f -print | wc -l
```

The '-type f' assumes that by 'items' you mean 'files' - remove it if you want to count directories as well

[I don't think -iname will match the directory (folderN) portion of the filepath]

---

### Post by alfirdaous on 2013-07-05
> **sandyd said:**
> use something like
```

find . \( -iname "*" ! -iname "folder2" ! -iname "folder3" \)
```

Thx, but it does not return the total

> **steeldriver said:**
> I would use a 'path prune' I think

```
find www \( -path 'www/folder2' -o -path 'www/folder3' \) -prune -o -type f -print | wc -l
```

The '-type f' assumes that by 'items' you mean 'files' - remove it if you want to count directories as well

[I don't think -iname will match the directory (folderN) portion of the filepath]

thx man, it's good, comparing ti total of find | wc -l , does not match

---

### Post by sandyd on 2013-07-06
```

find . | sed '/.\/2/d' |wc -l
```
That excludes
./2

```

find . | sed '/.\/2/d' |wc -l | sed '/.\/3/d'
```
That excludes
./2
./3

---

### Post by alfirdaous on 2013-07-08
in this case it's folder type "d", if we want to exclude even some files

---

