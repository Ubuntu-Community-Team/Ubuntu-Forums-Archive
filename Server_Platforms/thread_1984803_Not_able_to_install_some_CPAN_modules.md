---
title: "Not able to install some CPAN modules"
date: 2012-05-22
forum: Server Platforms
---

### Post by oliver2uk on 2012-05-22
Hi everyone,

I struggle to install few remaining perl modules in CPAN on my simple Ubuntu 10.04 server:

module BerkeleyDB is not installed      [FAILED]
module Crypt::OpenSSL::AES is not installed     [FAILED]
module DBD::ADO is not installed        [FAILED]
module DBD::Mimer is not installed      [FAILED]
module DBD::ODBC is not installed       [FAILED]
module PDF::GetImages is not installed  [FAILED]
module Image::OCR::Tesseract is not installed   [FAILED]
module PDF::OCR is not installed        [FAILED]
module PDF::OCR2 is not installed       [FAILED]

Ideally, I need the libraries installed via apt-get but I can't find them for the above. 

Basically, with all of the above I am getting results like the bellow:

Looking for /lib/libmimer.so...failed.
Couldn't find Mimer CLI/ODBC library at Makefile.PL line 78.
Warning: No success on command[/usr/bin/perl Makefile.PL INSTALLDIRS=site]
CPAN: YAML loaded ok (v0.81)
  MIMER/DBD-Mimer-1.00.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install     

Can anyone help please?

Oliver

---

### Post by a9k3d on 2012-05-24
Perl is telling you that it can't find the Mimer ODBC Driver. I haven't used Mimer yet but I didn't find the ODBC dirver using dpkg. Maybe you're using different rev of Ubuntu. You may have to download the Mimer ODBC code and compile it.

Another possibility is you have the library installed but PERL is looking in /lib/ while you've installed in /usr/lib/. Usually you can get around that by manually configuring the Perl module's build or symbolic linking the /usr/lib/ libmimer.so's in /lib/.

---

