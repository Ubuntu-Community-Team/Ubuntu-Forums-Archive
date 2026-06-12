---
title: "-fopenmp not working"
date: 2014-01-28
forum: Ubuntu Application Development
---

### Post by worm2 on 2014-01-28
[FONT=arial, sans-serif]I[/FONT][COLOR=#000000][FONT=Arial] am building the same application using the Intel MKL libraries and the GCC compiler, with all the flags advised by Intel. To use the GCC OMP implementation, -fopenmp is advised, which links the program with -lgomp. This works fine on Ubuntu 12.04 but on Ubuntu 13.10 GCC seems unable to find the right symbols. Anyone has a clue whether I am doing something wrong?
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
g++ -I$MKLROOT/include -I/home/jjgarcia/mps-bundle-gcc/include -g -O2 -fopenmp -o xy_stuck.exe xy_stuck.cc -O2 -L$MKLROOT/lib -L/home/jjgarcia/mps-bundle-gcc/lib -lmps -ltensor -lmkl_intel_lp64 -lmkl_core -lmkl_gnu_thread -ldl -lpthread -lf2c[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Adding -lgomp explicitly does not help, btw, and adding '-v' to the g++ flags does not reveal any interesting detail.[/FONT][/COLOR]

---

