---
title: "Minicom-2.2 install"
date: 2007-05-02
forum: Repositories &amp; Backports
---

### Post by Arch2 on 2007-05-02
I'm trying to install minicom-2.2 on Xubuntu with no luck. I got the source file form here... [http://alioth.debian.org/projects/minicom/](http://alioth.debian.org/projects/minicom/) then unzipped it on the desktop then ran their ./configure
it said i needed a compiler so i installed the gcc in the "Synapitic Package Manager"
now it says "C compiler cannot create executables See config.log"
there is says it cant find the default output filename confdefs.h failed.
Any suggestions
Thanks in advance

---

### Post by WW on 2007-05-03
You probably need more of the development packages than just gcc.  Install **build-essential**:
```

$ sudo apt-get install build-essential

```
and try again.

---

### Post by Hany935 on 2007-05-12
it&#347; worked , thanx ww

but when  I did  make ,anther problem appeared

it told me that many undefined references like :

....
..
.
                                                               
/home/hany935/Desktop/minicom-2.1/src/window.c:1625: undefined reference to `COLS'
/home/hany935/Desktop/minicom-2.1/src/window.c:1860: undefined reference to `tgetent'
................
...
.




i dont know why?

:confused:

---

### Post by WW on 2007-05-12
First, be sure that ./configure reports no errors before running make.  Then, when you run make, try to find the *first* error that is reported.  For example, an error about a missing header file (something like "header.h not found") is often followed by many "undefined reference" errors.

---

### Post by chrisclement on 2007-08-23
I am at about the same point. I installed gcc, ran configure w no errors and the 1st make. Everything hunky until the compiler is called in the src directory. 1st error is something about "too many arguments for tputs".

I will try to paste here:

make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/chris/Desktop/minicom-2.2/lib'
Making all in src
make[2]: Entering directory `/home/chris/Desktop/minicom-2.2/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -I../lib -DCONFDIR=\"/usr/local/etc\" -DLOCALEDIR=\"/usr/local/share/locale\"  -g -O2 -Wall -W -g -O2 -MT window.o -MD -MP -MF ".deps/window.Tpo" -c -o window.o window.c; \
        then mv -f ".deps/window.Tpo" ".deps/window.Po"; else rm -f ".deps/window.Tpo"; exit 1; fi
window.c: In function ‘outstr’:
window.c:195: error: too many arguments to function ‘tputs’
window.c: In function ‘_gotoxy’:
window.c:296: error: too many arguments to function ‘tgoto’

---

### Post by chrisclement on 2007-08-23
never mind ... go here and do these 3 quick steps. minicom is now working.

[http://www.strdoc.net/hyperterminal-replacement-ubuntu-minicom](http://www.strdoc.net/hyperterminal-replacement-ubuntu-minicom)

Apparently we aren't the only folks trying to communicate with an MRI and Microsoft/Intel took away the connectivity.

---

