---
title: "Compiling with libcurl"
date: 2009-05-31
forum: Ubuntu Dev Link Forum
---

### Post by halfpower on 2009-05-31
I'm trying to compile a program using libcurl.  I installed libcurl3, but I'm not sure if this is the right package.  I'm have this in my code:
```
#include <curl/curl.h>
```
but I get a lot of error messages such as 
```
getpage.c:16: error: ‘CURL’ undeclared (first use in this function)
```
when I try to compile.  Is the some compiler flag that I need to have on the command line when I compile?

---

### Post by johnl on 2009-06-01
Hi,

You need to install libcurl3-dev or libcurl4-dev to get the header files associated with the library.

When compiling, you should pass $(pkg-config --cflags libcurl) to gcc.  When linking, $(pkg-config --libs libcurl).  If you are compiling and linking in one step you can do it like so:

gcc myfile.c $(pkg-config --libs --cflags libcurl) -o myprogram

Hope this helps.

---

### Post by CannedCorn on 2010-08-27
This works:

```

gcc myfile.c $(pkg-config --libs --cflags libcurl) -o myprogram

```

But this would be easier to understand maybe?

```

gcc myfile.c -lcurl -o myprogram

```

Maybe someone could describe how they are different?

---

### Post by stevebu56 on 2010-09-07
> **CannedCorn said:**
> This works:

```

gcc myfile.c $(pkg-config --libs --cflags libcurl) -o myprogram

```

But this would be easier to understand maybe?

```

gcc myfile.c -lcurl -o myprogram

```

Maybe someone could describe how they are different?

Yes, that would be easier to understand but it hard codes the location of the curl library.  It has to be in /usr/lib or /usr/local/lib since those are the [default directories where gcc searches]("http://www.network-theory.co.uk/docs/gccintro/gccintro_21.html") for libraries.  What if I build the curl library from source and drop it in my home directory?  This is the problem that the pkg-config program alleviates.  When I build and install curl a [pkg-config]("http://pkg-config.freedesktop.org/wiki/") file is built based on where I installed curl then any other program can reference that file in order to include the headers or link to the libraries.  

Hope this clarifies things a little.

---

