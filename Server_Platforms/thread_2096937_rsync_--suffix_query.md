---
title: "rsync --suffix query"
date: 2012-12-21
forum: Server Platforms
---

### Post by maclenin on 2012-12-21
I run the following in the terminal:

```
/**testA**$ rsync -avr --suffix=_`date +"%m%d%Y_%H%M"` fileA.txt /**testB**/
```
In directory **testB**, I expect to find (a time-stamped):

**fileA.txt_12212012_1015**

Instead, in directory **testB**, I find (a non-time-stamped):

**fileA.txt**

Any thoughts?

---

### Post by maclenin on 2012-12-22
I stumbled upon my own oversight. All is fine with the rsync statement, as written. In my testy haste, I had forgotten to modify the contents of **fileA.txt** between runs....

HNY!

---

### Post by vanadium on 2012-12-22
You do not need the -r option as it is already part of the -a option. Yet, it does not hurt adding it, of course.

---

### Post by sudodus on 2012-12-22
I need the --backup option too:
```
rsync -av --backup --suffix=_`date +"%m%d%Y_%H%M"` "/home/$USER/test/ttt/" "/home/$USER/test/tbup/"
```

---

### Post by maclenin on 2012-12-23
**vanadium!**

Indeed, I had missed the "r" buried in the "a"....

**sudodus!**

After I discovered my "oversight", I was able to run my original statement without the -b (--backup) option and the added --suffix option still applied the date / time stamp, as defined.

Perhaps, the --suffix and --backup-dir options, when used in combination with the -b option redfine the -b defaults. However, --suffix, as seems to be the case in my original statement, can be used without -b to rename a changed destination file. Whereas, --backup-dir cannot be used independently of -b.

Thanks, again, for the guidance.

---

