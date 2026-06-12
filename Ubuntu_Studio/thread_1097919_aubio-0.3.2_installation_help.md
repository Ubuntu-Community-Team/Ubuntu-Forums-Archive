---
title: "aubio-0.3.2 installation help"
date: 2009-03-16
forum: Ubuntu Studio
---

### Post by propagation_of_sound on 2009-03-16
I am trying to compile Ardour 3. However, I need to install >=aubio-0.3.2 for it to work. I first looked it up on synaptic, but only aubio-tools was there (which I installed anyway, just to be sure). However there was no aubio. 
So I downloaded the source and compiled it. ./configure worked. At make however, I receive this error message: 

/usr/bin/ld: /usr/local/lib/libfftw3f.a(execute.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libfftw3f.a: could not read symbols: Bad value

This seemed to be something to do with fftw3 (which I had compiled earlier). Compiling was a success, as aubio's configure script found it on my system. 

I compiled both --enable-float and --disable-float to compile both single and double precision, and remembered to make clean between compiling each. 

I found execute.c in fftw-3.2.1/api/ of the source files, but I don't know how to recompile it with the -fPIC flag. 

I don't know where to go from here. 

I am using: *Ubuntu Studio 8.10 AMD64*

Thanks in advance.

---

### Post by propagation_of_sound on 2009-03-21
Anybody got any ideas please...? :(

---

### Post by jargel on 2009-06-19
to install all of ardour2's build dependencies, including aubio 0.4, try:

sudo apt-get build-dep ardour

---

### Post by Stochastic on 2009-06-19
> **jargel said:**
> to install all of ardour2's build dependencies, including aubio 0.4, try:

sudo apt-get build-dep ardour

The OP was looking to install Ardour 3 not Ardour 2.

But it looks like this task may be a little over his head (maybe not).  Aubio is in the repos a simple search ```
apt-cache search aubio
``` should return the libaubio-dev library that Ardour 3 requires.  No need to compile aubio from source.

It might be better to attempt compiling Ardour 3 in Jaunty rather than Intrepid (though I realize Jaunty wasn't out when the original post was made).

---

