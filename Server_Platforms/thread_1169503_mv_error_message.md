---
title: "mv error message"
date: 2009-05-25
forum: Server Platforms
---

### Post by salim.madni on 2009-05-25
dear gurus

i had try to move directory but it give me error can u tell mw what should i try for

root@mx1:/var/opt/backup/var/opt/axigen# mv /var/opt/backup/var/opt/axigen/* /var/opt/axigen


mv: cannot move `/var/opt/backup/var/opt/axigen/ctasd' to `/var/opt/axigen/ctasd': Directory not empty

regards

---

### Post by _Purple_ on 2009-05-25
Did you have ctasd inside /var/opt/axigen/ directory before moving the files?

---

### Post by Alekz_ on 2009-05-25
> **salim.madni said:**
> dear gurus

i had try to move directory but it give me error can u tell mw what should i try for

root@mx1:/var/opt/backup/var/opt/axigen# mv /var/opt/backup/var/opt/axigen/* /var/opt/axigen


mv: cannot move `/var/opt/backup/var/opt/axigen/ctasd' to `/var/opt/axigen/ctasd': Directory not empty

regards

If you intend to move a "directory", you must use '-R'!

```
mv -R /your/path/ /destiny/
```

PS.: '-R' means recursive

[]'s

---

### Post by _Purple_ on 2009-05-25
> **Alekz_ said:**
> If you intend to move a "directory", you must use '-R'!

```
mv -R /your/path/ /destiny/
```

PS.: '-R' means recursive

[]'s

The -R option is not available with mv. By default mv moves all the subdirectories as well.

---

### Post by Alekz_ on 2009-05-25
Sorry! My mistake! ;p

Forget about what I said... '-R' is for `cp`, not `mv`! :(

---

### Post by _Purple_ on 2009-05-25
No problem. We all make mistakes. :)

---

### Post by salim.madni on 2009-05-28
hello gurus

as i said you, on the source these folders are exists and on the desitnation it is not there, and on the source there is data/files/subfolder inside.

so everytime i try it get failed....

by giving your all option it moved only EMPTY FOLDERS FROM 1location to another location moved only.

can you advise what thing could be missing or any parameter files or folders issues.

this was original .tar.gz i unzip then start moving all files/folders from one to another location. but empty moved sucessfully and data occupied failure.

can you drill down more on this

regards
salim

---

### Post by _Purple_ on 2009-05-28
Hi Salim,
Try to use copy
```
cp -r /var/opt/backup/var/opt/axigen/* /var/opt/axigen
```

---

