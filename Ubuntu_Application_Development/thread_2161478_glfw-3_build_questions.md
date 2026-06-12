---
title: "glfw-3 build questions"
date: 2013-07-10
forum: Ubuntu Application Development
---

### Post by deepsender on 2013-07-10
hello,

I'm currently using glfw-2.7.8 successfully on many different versions of Linux.  Very easy to built glfw-2 using, "make x11".

Glfw-3 uses Cmake to construct the make files.  I cannot get it to work, as it is requiring many libraries during the process.

There is no documentation on building glfw-3, that I can find.

Please help me to get glfw-3 installed.

Ubuntu 12.04 64-bit is my current OS when writing this.

Thanks.

---

### Post by steeldriver on 2013-07-11
Where are you getting stuck exactly? I appear to have built it on my 32-bit 12.04 laptop (can't remember when or why!) so if you post back with specific questions I will try to point you in the right direction - it should be as simple as installing the prerequisite -dev packages, then creating a 'Build' subdirectory (not essential - just keeps the source tree tidy) then cd'ing into it and running 'cmake ../' and then make

---

### Post by Bram Stolk on 2013-08-08
I simply do
$ cmake .
$ make

---

### Post by MikeCyber on 2013-09-23
Thanks now I get:
/usr/bin/ld:  /usr/local/lib//libglfw3.a(context.c.o): relocation R_X86_64_32S against  `.rodata' can not be used when making a shared object; recompile with  -fPIC
/usr/local/lib//libglfw3.a: could not read symbols: Bad value

Hmm how to compile 3.02 with -fPIC? 
Thanks

---

