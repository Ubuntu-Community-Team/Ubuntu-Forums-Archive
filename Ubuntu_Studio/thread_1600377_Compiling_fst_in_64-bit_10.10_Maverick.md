---
title: "Compiling fst in 64-bit 10.10 Maverick"
date: 2010-10-18
forum: Ubuntu Studio
---

### Post by daveuu on 2010-10-18
Hi

I'd like to compile FST in Maverick 64. This may be a generic 'compile and use 32-bit in 64-bit OS' question but . . . having GIT cloned FST:

git clone git://repo.or.cz/fst.git

I get library errors on 'make' related to Jack: probably a no brainer but I don't really know what I'm doing ;-) Installing 'jackd1' and 'libjack-dev' via synaptic and necessarily removing 'jackd2' gets further (but breaks pulse-audio).

The remaining problems are:

```
/usr/bin/ld: skipping incompatible /usr/lib/libglib-2.0.so when searching for -lglib-2.0
/usr/bin/ld: skipping incompatible /usr/lib/libglib-2.0.a when searching for -lglib-2.0
/usr/bin/ld: skipping incompatible /usr/lib/liblash.so when searching for -llash
/usr/bin/ld: skipping incompatible /usr/lib/liblash.a when searching for -llash
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../liblash.so when searching for -llash
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../liblash.a when searching for -llash
/usr/bin/ld: skipping incompatible //usr/lib/liblash.so when searching for -llash
/usr/bin/ld: skipping incompatible //usr/lib/liblash.a when searching for -llash
/usr/bin/ld: cannot find -llash
/usr/bin/ld: skipping incompatible /lib/libdbus-1.so when searching for -ldbus-1
/usr/bin/ld: skipping incompatible /lib/libdbus-1.so when searching for -ldbus-1
```

I've searched hard on the web and have read passing references to successful 64-bit compiles, and possibly 64-bit pre-compiled packages in PPAs for previous Ubuntu versions (this is the first I've tried for music). AFAIK 64-bit Jack can take 32-bit clients (i.e., FST 32-bit)

Any pointers greatly appreciated,

Dave

---

