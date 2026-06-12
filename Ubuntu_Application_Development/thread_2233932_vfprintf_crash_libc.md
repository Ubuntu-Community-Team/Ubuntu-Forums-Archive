---
title: "vfprintf crash libc"
date: 2014-07-11
forum: Ubuntu Application Development
---

### Post by nibal on 2014-07-11
I use Ubuntu 10.34 64x. I am defining my own logging functions using vfprintf, but I am getting the following crash :-(:

```


Fri Jul 11 19:19:23 2014: Warn: 
Program received signal SIGSEGV, Segmentation fault.
0x00007ffff7841f90 in _IO_vfprintf_internal (s=<optimized out>, 
    format=<optimized out>, ap=<optimized out>) at vfprintf.c:1655
1655    vfprintf.c: No such file or directory.
(gdb) where
#0  0x00007ffff7841f90 in _IO_vfprintf_internal (s=<optimized out>, 
    format=<optimized out>, ap=<optimized out>) at vfprintf.c:1655
#1  0x00007ffff7843bff in buffered_vfprintf (
    s=s@entry=0x7ffff7bb71a0 <_IO_2_1_stderr_>, 
    format=format@entry=0x49d428 "%s ~> Unable to open logfile \"%s\" for writing (%d). %s. Using stderr\n", args=args@entry=0x7fffffffdac8) at vfprintf.c:2341
#2  0x00007ffff783e97e in _IO_vfprintf_internal (
    s=0x7ffff7bb71a0 <_IO_2_1_stderr_>, 
    format=0x49d428 "%s ~> Unable to open logfile \"%s\" for writing (%d). %s. Using stderr\n", ap=0x7fffffffdac8) at vfprintf.c:1307
#3  0x0000000000429df2 in warn (log=0x6a2100, 
    fmt=0x49d428 "%s ~> Unable to open logfile \"%s\" for writing (%d). %s. Using stderr\n") at logs.c:71
#4  0x000000000042a195 in logs_init () at logs.c:123
#5  0x0000000000407f8f in main (argc=1, argv=0x7fffffffde10) at vsmsc.l:1713


```

The C code that produces it is:

```

pthread_mutex_lock(&log->mutex);
date = ctime(&t);
date[24] = '\0';>.>..>..>..>..>..>..// '\n'
fprintf(log->fp, "%s: Warn: ", date);
va_start(args, fmt);
vfprintf(log->fp, fmt, args);
va_end(args);
pthread_mutex_unlock(&log->mutex);


```

As far as i can tell, this is an internal vfprintf error. All the arguments I pass to it are valid as evidenced by the stack trace and the preceeding fprintf statement.
If anyone knows anything about this vfprintf issue, I would appreciate some help.

TIA

---

### Post by nibal on 2014-07-11
Turns out that vfprintf works fine. Just doesn't report errors as it should, by not crashing. Error was somewhere else in the code, passing wrong number of args in varargs with respect to format. Unfortunately, gcc will not report any warnings or errors in this case, and you have to be carefull. :-)

---

### Post by ofnuts on 2014-07-13
When this kind of things happens I tend to be modest and consider first that I could be doing something wrong. The likeliness of my finding a blatant bug in a Linux library while doing simple things is below epsilon.

---

