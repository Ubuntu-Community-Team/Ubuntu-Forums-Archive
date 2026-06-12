---
title: "mir-doc in repos"
date: 2013-03-11
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-03-11
Just got an MIR update . 

Commit Log for Mon Mar 11 11:56:26 2013


Installed the following packages:
mir-doc (0.0.2bzr482raring0)


 But  now Nautilus will not search!

Where would I find it to examine it?

Thanks.

---

### Post by serdotlinecho on 2013-03-11
You can try search the path from terminal. Maybe, like this?:

```
dpkg -S mir-doc
or
locate mir-doc
```

---

### Post by kostkon on 2013-03-11
Maybe just give
```
man mir
```

---

### Post by ventrical on 2013-03-11
> **serdotlinecho said:**
> You can try search the path from terminal. Maybe, like this?:

```
dpkg -S mir-doc
```

Thanks..

/share/doc/mir-doc

a gazzilion files in there now :)

---

### Post by ventrical on 2013-03-13
Upgrades for MIR project comming in two days in a row now across the board for what is currently in the repos.

Has anybody found any more revisons in the hacking file that will point or instruct on how to do further demos of MIR using Raring? ie; terminal code

I had experimented with :

startx mir

and  I got a white box that flashed and went away and was easlily recoverable from.


Thanks.

---

