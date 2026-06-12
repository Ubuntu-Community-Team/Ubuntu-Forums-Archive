---
title: "Squid SSL Support"
date: 2007-03-13
forum: Server Platforms
---

### Post by badseed on 2007-03-13
Hi,
I am installing an reverse proxy using squid.
Tried with Dapper and Edgy, all went fine except for one thing.

When try to configure https_port there is a parser error (that meens ssl support was not compiled in squid), I confirmed it by downloading and compiling squid 2.6stable1 with --enable-ssl. Works fine.

But, what I really would like was for the package of Squid in Ubuntu to come with ssl-enabled, is it possible??
Can I add ssl-support to squid package (without having to compile from source)??



Thanks
João Mendes

---

### Post by Divan Santana on 2007-05-11
I tried to reconfigre the squid package to support the ssl option but it crashed strangely:

I did this:
apt-get source squid
apt-get  build-dep squid
apt-get install devscripts build-essential fakeroot
cd squid-2.6.1
vim debian/rules
Add --enable-follow-x-forwarded-for \ to &#8220;# Configure the package&#8221; section
Add --enable-ssl \ to &#8220;# Configure the package&#8221; section
./configure
debuild -us -uc -b

It bombed out with the following error:

> In file included from rfc2617.c:52:
../include/md5.h:14:2: error: #error Cannot find OpenSSL headers
rfc2617.c: In function &#8216;DigestCalcHA1&#8217;:
rfc2617.c:110: error: &#8216;MD5_CTX&#8217; undeclared (first use in this function)
rfc2617.c:110: error: (Each undeclared identifier is reported only once
rfc2617.c:110: error: for each function it appears in.)
rfc2617.c:110: error: expected &#8216;;&#8217; before &#8216;Md5Ctx&#8217;
rfc2617.c:113: warning: implicit declaration of function &#8216;MD5_Init&#8217;
rfc2617.c:113: error: &#8216;Md5Ctx&#8217; undeclared (first use in this function)
rfc2617.c:114: warning: implicit declaration of function &#8216;MD5_Update&#8217;
rfc2617.c:119: warning: implicit declaration of function &#8216;MD5_Final&#8217;
rfc2617.c: In function &#8216;DigestCalcResponse&#8217;:
rfc2617.c:147: error: &#8216;MD5_CTX&#8217; undeclared (first use in this function)
rfc2617.c:147: error: expected &#8216;;&#8217; before &#8216;Md5Ctx&#8217;
rfc2617.c:154: error: &#8216;Md5Ctx&#8217; undeclared (first use in this function)
make[2]: *** [rfc2617.o] Error 1
make[2]: Leaving directory `/root/squid-2.6.5/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/squid-2.6.5'
make: *** [build] Error 2
debuild: fatal error at line 1228:
debian/rules build failed

---

### Post by MJN on 2007-05-12
> **badseed said:**
> But, what I really would like was for the package of Squid in Ubuntu to come with ssl-enabled, is it possible??

No, unfortunately. The OpenSSL and Squid licences are not compatible hence cannot be distributed as a compiled package.

Mathew

---

### Post by briealeida on 2007-05-16
According to squid-cache.org, Squid 3.0 will have SSL support. Will Ubuntu upgrade?

---

### Post by MJN on 2007-05-16
Not in Edgy.

Mathew

---

### Post by Df_Yz on 2007-12-25
> **Divan Santana said:**
> 
...
In file included from rfc2617.c:52:
../include/md5.h:14:2: error: _**#error Cannot find OpenSSL headers**_
rfc2617.c: In function ‘DigestCalcHA1’:
....

Bg.. Did you read error message?
You need to install -dev packages of OpenSSl.

---

