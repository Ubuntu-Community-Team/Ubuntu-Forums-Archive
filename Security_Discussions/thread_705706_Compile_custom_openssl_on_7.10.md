---
title: "Compile custom openssl on 7.10?"
date: 2008-02-23
forum: Security Discussions
---

### Post by JohnDewey on 2008-02-23
Hi folks,

I'm new to this forum and also relatively new to Ubuntu, though not to Linux and Unix in general. Anyway, I'm trying to port a programm I've written on OS X and now I have a question regarding openssl:

I need openssl with Camellia-256 activated as a block cipher, but the install from synaptic doesn't have this cipher enabled.

Is it okay to manually compile and install openssl on Ubuntu 7.10 or might this mess up my system? Or is there a way to get openssl with Camellia via some repository?

BTW, on OS X it wasn't switched on by default either and I compiled it manually.

---

### Post by bwhite82 on 2008-02-23
I see no reason why you couldn't compile it yourself, after removing the package first.

---

### Post by kevdog on 2008-02-24
I managed to compile openssl from cvs on cygwin, so I don't think it would be any problem on a real linux system.  I know about the camellia cipher within gnupg, however I haven't done this with openssl.  I'm not sure if its included in the the config options?  Is this code going to be custom?

Update

Take that back.  The newest cvs Im getting this:
ocsp.c: In function `query_responder':
ocsp.c:1258: error: storage size of 'tv' isn't known
ocsp.c:1286: warning: implicit declaration of function `select'
ocsp.c:1258: warning: unused variable `tv'
make[1]: *** [ocsp.o] Error 1
make[1]: Leaving directory `/home/klal/temp/openssl/openssl_svn/openssl/apps'
make: *** [build_apps] Error 1

---

### Post by JohnDewey on 2008-02-24
The code is not custom, if I remember correctly it's a config option that for some reason isn't switched on by default. (I wonder why, as nobody is forced to use the cipher when it is enabled, but I guess the openssl people have their reasons.)

So I'll just remove the package and compile it for myself from CVS. :)

Thanks for the quick replies!

Edit: Ooops, I've just seen the update to your latest post. So it might not work. Anyway, I'll give it a try myself.

---

### Post by kevdog on 2008-02-24
Let me know how you make out -- Id be really interested.  For camellia its probably something like --enable-camellia

---

