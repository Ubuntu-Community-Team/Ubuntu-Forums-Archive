---
title: "curses/ncurses"
date: 2012-06-25
forum: Ubuntu Application Development
---

### Post by zariro on 2012-06-25
hie i am having problems with compiling a c program that uses curses.h. i am using the gedit text editor on ubuntu 12.04. i installed gcc compiler, i have tried google but when i try the examples the do not seem to work all i get are errors of undefined functions like the initscr.

Can any one help please maybe with a link to a tutorial that can help me through.

---

### Post by Namibnat on 2012-07-23
use the -lncurses flag in your compilation:

```
gcc -o simple simple.c -lncurses
```

---

