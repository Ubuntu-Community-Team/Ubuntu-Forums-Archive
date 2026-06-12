---
title: "libapreq2-2.13 install problem"
date: 2011-08-27
forum: Server Platforms
---

### Post by meastwood on 2011-08-27
Up-to-date generic ubuntu desktop with apache2 installed (via package manager)

Am looking to write mod_perl 2.0 handlers (am a newbie in this area).  It looks to me that to handle post/get data I need the Apache2::Request module installed - am not wanting to use CGI.pm or Modperl::Registry.

So attempted to install Apache2::Request via CPAN and get the following:
cpan[1]> install Apache2::Request
CPAN: Storable loaded ok (v2.20)
Reading '/root/.local/share/.cpan/Metadata'
  Database was generated on Sun, 28 Aug 2011 00:28:09 GMT
Running install for module 'Apache2::Request'
Running make for I/IS/ISAAC/libapreq2-2.13.tar.gz
CPAN: Digest::SHA loaded ok (v5.47)
CPAN: Compress::Zlib loaded ok (v2.02)
Checksum for /root/.local/share/.cpan/sources/authors/id/I/IS/ISAAC/libapreq2-2.13.tar.gz ok
Scanning cache /root/.local/share/.cpan/build for sizes
............................................................................DONE
CPAN: Archive::Tar loaded ok (v1.52)
libapreq2-2.13/acinclude.m4
libapreq2-2.13/aclocal.m4
.......... (removed for brevity - no errors reported)
libapreq2-2.13/win32/util.pl
CPAN: File::Temp loaded ok (v0.22)
CPAN: Parse::CPAN::Meta loaded ok (v1.39)

  CPAN.pm: Building I/IS/ISAAC/libapreq2-2.13.tar.gz

perl: 5.10.1 ok
mod_perl2: 2.000004 ok
Apache::Test: 1.31 ok
ExtUtils::MakeMaker: 6.55 ok
ExtUtils::XSBuilder: 0.28 ok
Test::More: 0.92 ok
./configure --enable-perl-glue --with-perl-opts="INSTALLDIRS=site" --with-apache2-apxs="/usr/bin/apxs2" --with-perl="/usr/bin/perl"
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
.......... (removed for brevity - no errors reported)
checking whether ln -s works... yes
checking whether to enable maintainer-specific portions of Makefiles... no
Can't open perl script "INSTALLDIRS=site": No such file or directory
configure: error: Bad apache2 binary (/usr/sbin/apache2)
Warning: No success on command[/usr/bin/perl Makefile.PL INSTALLDIRS=site]
'YAML' not installed, will not store persistent state
  ISAAC/libapreq2-2.13.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
Could not read metadata file. Falling back to other methods to determine prerequisites
Failed during this command:
 ISAAC/libapreq2-2.13.tar.gz                  : writemakefile NO '/usr/bin/perl Makefile.PL INSTALLDIRS=site' returned status 256

Am I missing something from the Apache2 server install or the Environment ain't right.

cheers

---

### Post by meastwood on 2011-08-28
Well yes and no.

Simply used the Ubuntu libapreq2 package and installed via Apt. 

Does concern me that I cannot use CPAN reliably (on ubuntu).

---

### Post by DavidBooth on 2011-11-25
I am having the same problem and have not yet found a solution.  Attempts to install Apache2::Request via cpan failed with this message:
[[
[ . . . ]
checking whether to enable maintainer-specific portions of Makefiles... no
./configure: line 20252: /usr/bin/apxs2: No such file or directory
./configure: line 20266: /usr/bin/apxs2: No such file or directory
./configure: line 20270: /usr/bin/apxs2: No such file or directory
./configure: line 20274: /usr/bin/apxs2: No such file or directory
./configure: line 20274: /usr/bin/apxs2: No such file or directory
Can't open perl script "INSTALLDIRS=site": No such file or directory
configure: error: Bad apache2 binary (/)
Warning: No success on command[/usr/bin/perl Makefile.PL INSTALLDIRS=site]
  ISAAC/libapreq2-2.13.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
Could not read metadata file. Falling back to other methods to determine prerequisites
Failed during this command:
 ISAAC/libapreq2-2.13.tar.gz                  : writemakefile NO '/usr/bin/perl Makefile.PL INSTALLDIRS=site' returned status 256
]]

I then ran Synaptic Package Manager and installed libapreq2.  But when I subsequently try again to install Apache2::Request using cpan I get:
[[
cpan[10]> install Apache2::Request
Running install for module 'Apache2::Request'
Running make for I/IS/ISAAC/libapreq2-2.13.tar.gz
  Has already been unwrapped into directory /home/dbooth/.cpan/build/libapreq2-2.13-41MKPB
  '/usr/bin/perl Makefile.PL INSTALLDIRS=site' returned status 256, won't make
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
]]

I notice that the libapreq2 version that I installed was 2.08-5.1, whereas cpan seems to be trying to install version 2.13-41MKPB.  I do not know whether that is an issue. I tried removing (actually renaming) the libapreq2-2.13-41MKPB files that cpan had downloaded, in the hope that it would pick up the version of libapreq2 that I had installed via Synaptic, but that made no difference.

Anyone know how I can get Apache2::Request installed correctly?

I'm on Ubuntu 10.04.

---

