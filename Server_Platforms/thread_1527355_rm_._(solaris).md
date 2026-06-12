---
title: "rm *. (solaris)"
date: 2010-07-09
forum: Server Platforms
---

### Post by isshalor on 2010-07-09
Hey Guys,
 
I messed up earlier and did a touch *. instead of a touch *.txt. Now I have a file that is a *. and I can't remove it. I don't want to to do a rm *. because that might remove a bunch other files. Any tips on removing that file safely.
 
Thanks

---

### Post by sisco311 on 2010-07-09
You have to escape the *:

```
rm -i \*.
```
```
rm -i '*.'
```

See:```
man bash | less +/^QUOTING
```


BTW, only *. matches files with a . (period) at the end of the filename.

---

### Post by isshalor on 2010-07-09
Thanks guys that worked.. just unsure when using a rm with anthing like a *.
 
Thanks

---

