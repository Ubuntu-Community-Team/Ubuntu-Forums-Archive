---
title: "CPAN: couldn't untar"
date: 2007-06-11
forum: Server Platforms
---

### Post by stunti on 2007-06-11
I try for some time now to install DKIM proxy on my server.
But each time I try to install a perl package, it failed the same way.
This is for Crypt::OpenSSL::RSA, but it always end the same way for any packages.
I have installed build-essential.

Any ideas ?
Thanks

```

 cpan> install Crypt::OpenSSL::RSA
CPAN: Storable loaded ok
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  ftp://ftp.perl.org/pub/CPAN/authors/01mailrc.txt.gz
Going to read /home/stunti/.cpan/sources/authors/01mailrc.txt.gz
CPAN: Compress::Zlib loaded ok
Fetching with LWP:
  ftp://ftp.perl.org/pub/CPAN/modules/02packages.details.txt.gz
Going to read /home/stunti/.cpan/sources/modules/02packages.details.txt.gz
  Database was generated on Mon, 11 Jun 2007 06:08:30 GMT

  There's a new CPAN.pm version (v1.9102) available!
  [Current version is v1.7602]
  You might want to try
    install Bundle::CPAN
    reload cpan
  without quitting the current session. It should be a seamless upgrade
  while we are running...

Fetching with LWP:
  ftp://ftp.perl.org/pub/CPAN/modules/03modlist.data.gz
Going to read /home/stunti/.cpan/sources/modules/03modlist.data.gz
Going to write /home/stunti/.cpan/Metadata
Running install for module Crypt::OpenSSL::RSA
Running make for I/IR/IROBERTS/Crypt-OpenSSL-RSA-0.25.tar.gz
Fetching with LWP:
  ftp://ftp.perl.org/pub/CPAN/authors/id/I/IR/IROBERTS/Crypt-OpenSSL-RSA-0.25.tar.gz
CPAN: Digest::MD5 loaded ok
Fetching with LWP:
  ftp://ftp.perl.org/pub/CPAN/authors/id/I/IR/IROBERTS/CHECKSUMS
Checksum for /home/stunti/.cpan/sources/authors/id/I/IR/IROBERTS/Crypt-OpenSSL-RSA-0.25.tar.gz ok
Scanning cache /home/stunti/.cpan/build for sizes
Use of uninitialized value in chdir at /usr/share/perl/5.8/CPAN.pm line 928.
Use of chdir('') or chdir(undef) as chdir() is deprecated at /usr/share/perl/5.8/CPAN.pm line 928.
Uncompressed /home/stunti/.cpan/sources/authors/id/I/IR/IROBERTS/Crypt-OpenSSL-RSA-0.25.tar.gz successfully
Using Tar:/bin/tar xvf /home/stunti/.cpan/sources/authors/id/I/IR/IROBERTS/Crypt-OpenSSL-RSA-0.25.tar:
Couldn't untar /home/stunti/.cpan/sources/authors/id/I/IR/IROBERTS/Crypt-OpenSSL-RSA-0.25.tar


```

---

### Post by tr333 on 2007-06-12
try downloading the Crypt::OpenSSL::RSA module directly from [http://search.cpan.org/~iroberts/Crypt-OpenSSL-RSA-0.25/RSA.pm]("http://search.cpan.org/~iroberts/Crypt-OpenSSL-RSA-0.25/RSA.pm"), then installing it with:
```
$ perl Makefile.pl
$ make
$ make test
$ make install

```

the "make test" should tell you if it requires any other dependencies.
I have always found the cpan shell to be a bit buggy, so why not try its replacement CPANPLUS.  This can be installed from cpan with "install Bundle::CPANPLUS" or by downloading from cpan.org as with the above module.  the commandline shell for this is "cpanp" instead of "cpan" for the original cpan shell.

---

### Post by stunti on 2007-06-12
Thanks a lot.
I can't get cpanplus working but dkim is now working well and my email are not marked as spam by gmail.
I'm happy.
thanks

---

