---
title: "cannot find crt1.o:"
date: 2021-04-29
forum: Repositories &amp; Backports
---

### Post by meocomandante on 2021-04-29
I'm compiling a program based on f77 and I get that 

[HTML]/usr/bin/ld: cannot find crt1.o: No such file or directory
/usr/bin/ld: cannot find crti.o: No such file or directory
collect2: ld returned 1 exit status[/HTML]

crt1.o and crt0.o both are in 
[HTML]/usr/mipsel-linux-gnu/lib/crt1.o
/usr/lib/x86_64-linux-gnu/crt1.o
[/HTML]

even after add path to bashrc
[HTML]Library_PATH=/usr/lib/x86_64-linux-gnu:$LIBRARY_PATH
export LIBRARY_PATH[/HTML]

I'm getting crazy with this error.
Does anyone have a solution to this problem?

my system is lubuntu 18.04.05

---

### Post by Xian on 2021-04-29
You may just need to install the gcc for mutlilib support

```
[FONT=inherit]sudo apt install gcc-multilib[/FONT]
```

---

