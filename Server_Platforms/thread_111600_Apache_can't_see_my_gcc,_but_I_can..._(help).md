---
title: "Apache can't see my gcc, but I can... (help)"
date: 2006-01-02
forum: Server Platforms
---

### Post by aquaboot on 2006-01-02
Hi All,

I've downloaded httpd from apache.org and am trying to compile it.  It complains that it can't find any suitable c compilers:

checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH

My gcc is in /usr/lib:

root@darklight:~# whereis gcc
gcc: /usr/lib/gcc

/usr/lib is in my $PATH:

root@darklight:~# echo $PATH
/usr/lib:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11

I even tried drilling down to the actual compiler location in /usr/lib/gcc and tweaking my path again: (I've also tried just putting /usr/lib/gcc in my $PATH to no avail)

echo $PATH
/usr/lib/gcc/i486-linux-gnu/4.0.2/cc1:/usr/local/sbin:/usr/local/bin:/usr/sbin:/

While trying to ./configure, apache still complains it can't find the c compiler.  

Any Ideas?

Help Much Appreciated,

ab

---

### Post by lisje on 2006-01-02
why are you trying to install apache from source? the package in the ubuntu repositories are fine.. for more info look here: [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

you could still try to install the "build-essential"-package first if you still want to try installing apache from source ... you might have more succes then...

---

