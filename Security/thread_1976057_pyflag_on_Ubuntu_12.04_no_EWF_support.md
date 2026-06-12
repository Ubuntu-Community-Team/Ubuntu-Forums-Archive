---
title: "pyflag on Ubuntu 12.04 no EWF support"
date: 2012-05-08
forum: Security
---

### Post by felixdzerzhinsky on 2012-05-08
Trying to compile pyflag with EWF support. (PyFlag is a web-based, database-backed forensic and log analysis GUI and Computer forensics framework written in Python. PyFlag stores disk images in numerous file formats, including raw, sgzip, AFF, and EnCase format.)

I have tried both install the libewf package and compiling from source.

EWF is clearly installed.

```
root@gUn:~/Downloads/libewf-20120504# ewfinfo -V
ewfinfo 20120504

Copyright (c) 2006-2012, Joachim Metz <jbmetz@users.sourceforge.net>.
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
root@gUn:~/Downloads/libewf-20120504# 
```

But when I try to configure pyflag I get:

```
configure: 
configure: *****************************************
configure: PyFlag pyflag 0.87-pre1 configuration
configure: EWF Support:             no 
configure: AFF Support:             yes 
configure: MaxMind GeoIP:           yes 
configure: Advanced JpegCarving:    yes 
configure: *****************************************
configure: 
felixdz@gUn:~/forensics/pyflag$ 
```

I see looking up:

```
checking for libewf_open in -lewf... yes
configure: WARNING: You libewf version must be more recent then 20080501.
checking GeoIP.h usability... yes

```

One would think that libewf version 20120504 must be more recent then 20080501. 

Is there a work around for this?

---

### Post by irapuanp on 2012-06-03
HI.

I found the correct libewf version at devel site.

[http://sourceforge.net/projects/libewf/files/libewf/libewf-20080501/](http://sourceforge.net/projects/libewf/files/libewf/libewf-20080501/)

Simples, remove any other version that you have add by apt-get and install these version (dpgk). You'll need libssl and python.mysql. When you try to install these packages, you'll see the correct system package needs.

These step I already pass, but I found a problem pyaff compilation.
First it not found the afflib.h. I copied it from /usr/lib/include to src/lib/pyaff.

Now I have this issue:

```
Making all in pyaff
make[3]: Entering directory `/home/irapuan/Downloads/pyflag/pyflag-0.87-pre1/src/lib/pyaff'
/bin/bash ../../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../../src/include -I../../../src/filesystems/sleuthkit/sleuthkit-2.52/tsk  -I/usr/include/python2.7  -include config.h -g -O2 -MT pyaff_la-pyaff.lo -MD -MP -MF .deps/pyaff_la-pyaff.Tpo -c -o pyaff_la-pyaff.lo `test -f 'pyaff.c' || echo './'`pyaff.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../../../src/include -I../../../src/filesystems/sleuthkit/sleuthkit-2.52/tsk -I/usr/include/python2.7 -include config.h -g -O2 -MT pyaff_la-pyaff.lo -MD -MP -MF .deps/pyaff_la-pyaff.Tpo -c pyaff.c  -fPIC -DPIC -o .libs/pyaff_la-pyaff.o
pyaff.c: In function ‘affile_init’:
pyaff.c:109:26: error: dereferencing pointer to incomplete type
make[3]: *** [pyaff_la-pyaff.lo] Error 1
make[3]: Leaving directory `/home/irapuan/Downloads/pyflag/pyflag-0.87-pre1/src/lib/pyaff'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/irapuan/Downloads/pyflag/pyflag-0.87-pre1/src/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/irapuan/Downloads/pyflag/pyflag-0.87-pre1/src'
make: *** [all-recursive] Error 1

```

Irapuan Menezes

---

### Post by irapuanp on 2012-06-03
Hi again.

I do an adjust into source src/lib/pyaff/pyaff.c and I can make.

It is works now.

The adjust is:

```

static int
affile_init(affile *self, PyObject *args, PyObject *kwds) {
        char *filename;
    static char *kwlist[] = {"filename", NULL};

    self->size = 0;

    if(!PyArg_ParseTupleAndKeywords(args, kwds, "s", kwlist, &filename))
        return -1;

    self->af = af_open(filename, O_RDONLY, 0);
    if(self->af == NULL) {
        PyErr_Format(PyExc_IOError, "Failed to initialise afflib");
        return -1;
    }

    // Irapuan HACKS
    // I discomment the bellow line and comment the line bellow it.
    self->size = af_get_imagesize(self->af);
    //self->size = self->af->image_size;
    return 0;
}

```

Irapuan Menezes

---

