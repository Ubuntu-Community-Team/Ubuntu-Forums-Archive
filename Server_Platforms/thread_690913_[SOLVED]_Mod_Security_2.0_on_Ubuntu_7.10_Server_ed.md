---
title: "[SOLVED] Mod_Security 2.0 on Ubuntu 7.10 Server edition"
date: 2008-02-07
forum: Server Platforms
---

### Post by il3dsm on 2008-02-07
Sorry if this is the wrong forum for it, but I'm having difficulty installing Mod_Security on Ubuntu 7.10 Server Edition.

I've searched on google but can't find a solution, so I'm posting here.

Here's an output I'm getting. I'm not a Linux guru obviously but as far as I know it can't find a command. I get this error when doing "make", prior to "make install".

/usr/share/apr-1.0/build/libtool --silent --mode=compile i486-linux-gnu-gcc   -O2 -g -Wuninitialized -Wall -Wmissing-prototypes -Wshadow -Wunused-variable -Wunused-value -Wchar-subscripts -Wsign-compare -DWITH_LIBXML2   -DLINUX=2 -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -D_REENTRANT -I/usr/include/apache2 -I. -I/usr/include/apr-1.0 -I/usr/include/postgresql  -I /usr/include/libxml2 -I/usr/include/apache2 -I. -I/usr/include/apr-1.0 -I/usr/include/postgresql -prefer-pic -c mod_security2.c && touch mod_security2.slo
/usr/share/apr-1.0/build/libtool: line 1222: i486-linux-gnu-gcc: command not found
make: *** [mod_security2.slo] Error 1

Side note: Everything worked fine in Ubuntu 7.10 desktop edition. :(

Help.

---

### Post by faulkes on 2008-02-08
This is the right place.

There error seems to relate to libtool not being able to find gcc (i486-linux-gnu-gcc to be specific).  GCC is the compiler.

There are a number of possible reasons for this;

1. gcc or i486-linux-gnu-gcc are not in your path.
```

whereis gcc
or
whereis i486-linux-gnu-gcc

```

If it returns a path to gcc, you can add it into your path via

```

PATH=$PATH:/path/to/
export PATH

```

2. You do not have gcc installed.
- I'm not sure of the apt-get command line to install gcc (I originally put here to use synaptic,
but being 2am, I also forgot the server doesn't ship with X installed).

Faulkes

---

### Post by il3dsm on 2008-02-08
Problem was solved after I've installed gcc, thanks for helping me.

---

