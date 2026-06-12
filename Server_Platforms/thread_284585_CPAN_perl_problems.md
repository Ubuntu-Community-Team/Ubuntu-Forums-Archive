---
title: "CPAN perl problems"
date: 2006-10-25
forum: Server Platforms
---

### Post by malder on 2006-10-25
I am trying to install some perl modules with CPAN and am having problems. Here is what I'm getting:

```
cpan> install Digest::SHA1
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Wed, 25 Oct 2006 18:24:36 GMT
Running install for module Digest::SHA1
Running make for G/GA/GAAS/Digest-SHA1-2.11.tar.gz
CPAN: Digest::MD5 loaded ok
Checksum for /root/.cpan/sources/authors/id/G/GA/GAAS/Digest-SHA1-2.11.tar.gz okScanning cache /root/.cpan/build for sizes
Digest-SHA1-2.11/
Digest-SHA1-2.11/README
Digest-SHA1-2.11/t/
Digest-SHA1-2.11/t/bits.t
Digest-SHA1-2.11/t/badfile.t
Digest-SHA1-2.11/t/sha1.t
Digest-SHA1-2.11/MANIFEST
Digest-SHA1-2.11/fip180-1.html
Digest-SHA1-2.11/SHA1.pm
Digest-SHA1-2.11/typemap
Digest-SHA1-2.11/fip180-1.gif
Digest-SHA1-2.11/Changes
Digest-SHA1-2.11/Makefile.PL
Digest-SHA1-2.11/SHA1.xs
Removing previously used /root/.cpan/build/Digest-SHA1-2.11

  CPAN.pm: Going to build G/GA/GAAS/Digest-SHA1-2.11.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for Digest::SHA1
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible

```

This is while following the Qmailrocks.org guide for Debian.

Thanks for the help.

---

### Post by MyAnda on 2006-10-25
make sure you have everything and try again

apt-get install make gcc zlib1g-dev

---

### Post by ziggie216 on 2007-06-10
having the same problem

---

### Post by Mr. C. on 2007-06-11
Install the build-essential package.

MrC

---

