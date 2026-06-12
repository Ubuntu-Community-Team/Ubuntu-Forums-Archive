---
title: "Installing bugzilla and DateTime problem"
date: 2009-12-02
forum: Server Platforms
---

### Post by E.Hyde on 2009-12-02
Hi to all, i'm newbie on linux world, so, sorry for my questions, maybe stupid for you.

I'm trying to install bugzilla on my first ubuntu server and i have some errors that i'm not able to solved also readings [this](http://ubuntuforums.org/showthread.php?p=8379485) thread.

This is the output of command checksetup.pl --check-modules

```

Checking perl modules...
Checking for              CGI.pm (v3.33)   ok: found v3.48 
Checking for          Digest-SHA (any)     ok: found v5.45 
Checking for            TimeDate (v2.21)   ok: found v2.22 
Checking for            DateTime (v0.28)    not found 
Checking for   DateTime-TimeZone (v0.71)    not found 
Checking for                 DBI (v1.41)   ok: found v1.609 
Checking for    Template-Toolkit (v2.22)    not found 
Checking for          Email-Send (v2.00)   ok: found v2.198 
Checking for          Email-MIME (v1.861)  ok: found v1.902 
Checking for Email-MIME-Encodings (v1.313)  ok: found v1.313 
Checking for Email-MIME-Modifier (v1.442)  ok: found v1.902 
Checking for                 URI (any)     ok: found v1.37 

Checking available perl DBD modules...
Checking for              DBD-Pg (v1.45)    not found 
Checking for           DBD-mysql (v4.00)   ok: found v4.011 
Checking for          DBD-Oracle (v1.19)    not found 

The following Perl modules are optional:
Checking for                  GD (v1.20)    not found 
Checking for               Chart (v1.0)     not found 
Checking for         Template-GD (any)      not found 
Checking for          GDTextUtil (any)      not found 
Checking for             GDGraph (any)      not found 
Checking for            XML-Twig (any)     ok: found v3.32 
Checking for          MIME-tools (v5.406)  ok: found v5.427 
Checking for         libwww-perl (any)     ok: found v5.829 
Checking for         PatchReader (v0.9.4)  ok: found v0.9.5 
Checking for          PerlMagick (any)      not found 
Checking for           perl-ldap (any)     ok: found v0.39 
Checking for         Authen-SASL (any)     ok: found v2.13 
Checking for          RadiusPerl (any)     ok: found v0.15 
Checking for           SOAP-Lite (v0.710.06) ok: found v0.710.10 
Checking for         HTML-Parser (v3.40)   ok: found v3.61 
Checking for       HTML-Scrubber (any)     ok: found v0.08 
Checking for Email-MIME-Attachment-Stripper (any)     ok: found v1.316 
Checking for         Email-Reply (any)     ok: found v1.202 
Checking for         TheSchwartz (any)     ok: found v1.07 
Checking for      Daemon-Generic (any)     ok: found v0.61 
Checking for            mod_perl (v1.999022)  not found 

```

I don't want optional modules related to GUI cose actually i'm working without a GUI, but i need times modules.
So tryed to install DateTime using install-module.pl DateTime and these are the errors:

```

CPAN: Storable loaded ok (v2.18)
Going to read /home/cruggeri/.cpan/Metadata
  Database was generated on Wed, 02 Dec 2009 13:39:09 GMT
Installing DateTime version 0.51...
Running install for module 'DateTime'
'YAML' not installed, falling back to Data::Dumper and Storable to read prefs '/home/cruggeri/.cpan/prefs'
Running make for D/DR/DROLSKY/DateTime-0.51.tar.gz
CPAN: Digest::SHA loaded ok (v5.45)
CPAN: Compress::Zlib loaded ok (v2.008)
Checksum for /home/cruggeri/.cpan/source/authors/id/D/DR/DROLSKY/DateTime-0.51.tar.gz ok
DateTime-0.51
DateTime-0.51/META.yml
DateTime-0.51/Changes
DateTime-0.51/README
DateTime-0.51/TODO
DateTime-0.51/MANIFEST
DateTime-0.51/CREDITS
DateTime-0.51/SIGNATURE
DateTime-0.51/leaptab.txt
DateTime-0.51/LICENSE
DateTime-0.51/Build.PL
DateTime-0.51/t
DateTime-0.51/t/35rd_values.t
DateTime-0.51/t/15jd.t
DateTime-0.51/t/42duration_class.t
DateTime-0.51/t/27delta.t
DateTime-0.51/t/02last_day.t
DateTime-0.51/t/31formatter.t
DateTime-0.51/t/01sanity.t
DateTime-0.51/t/22from_doy.t
DateTime-0.51/t/03components.t
DateTime-0.51/t/21bad_params.t
DateTime-0.51/t/41cldr_format.t
DateTime-0.51/t/20infinite.t
DateTime-0.51/t/39no-so.t
DateTime-0.51/t/19leap_second.t
DateTime-0.51/t/28dow.t
DateTime-0.51/t/38local-subtract.t
DateTime-0.51/t/06add.t
DateTime-0.51/t/pod.t
DateTime-0.51/t/11duration.t
DateTime-0.51/t/26dt_leapsecond_pm.t
DateTime-0.51/t/37local-add.t
DateTime-0.51/t/36invalid_local.t
DateTime-0.51/t/10subtract.t
DateTime-0.51/t/40leap-years.t
DateTime-0.51/t/00load.t
DateTime-0.51/t/05set.t
DateTime-0.51/t/07compare.t
DateTime-0.51/t/04epoch.t
DateTime-0.51/t/12week.t
DateTime-0.51/t/09greg.t
DateTime-0.51/t/16truncate.t
DateTime-0.51/t/17set_return.t
DateTime-0.51/t/18today.t
DateTime-0.51/t/30future_tz.t
DateTime-0.51/t/13strftime.t
DateTime-0.51/t/32leap_second2.t
DateTime-0.51/t/33seconds_offset.t
DateTime-0.51/t/24from_object.t
DateTime-0.51/t/pod-coverage.t
DateTime-0.51/t/29overload.t
DateTime-0.51/t/34set_tz.t
DateTime-0.51/t/23storable.t
DateTime-0.51/t/25add_subtract.t
DateTime-0.51/t/14locale.t
DateTime-0.51/tools
DateTime-0.51/tools/leap_seconds_header.pl
DateTime-0.51/c
DateTime-0.51/c/leap_seconds.h
DateTime-0.51/c/ppport.h
DateTime-0.51/lib
DateTime-0.51/lib/DateTime.xs
DateTime-0.51/lib/DateTime.pm
DateTime-0.51/lib/DateTimePPExtra.pm
DateTime-0.51/lib/DateTimePP.pm
DateTime-0.51/lib/DateTime
DateTime-0.51/lib/DateTime/Duration.pm
DateTime-0.51/lib/DateTime/Infinite.pm
DateTime-0.51/lib/DateTime/Helpers.pm
DateTime-0.51/lib/DateTime/LeapSecond.pm
CPAN: File::Temp loaded ok (v0.18)
CPAN: Time::HiRes loaded ok (v1.9711)
Warning (usually harmless): 'YAML' not installed, will not store persistent state

  CPAN.pm: Going to build D/DR/DROLSKY/DateTime-0.51.tar.gz

Checking whether your kit is complete...
Looks good

Checking prerequisites...
Creating new 'Build' script for 'DateTime' version '0.51'
Could not read '/home/cruggeri/.cpan/build/DateTime-0.51-19Gkau/META.yml'. Falling back to other methods to determine prerequisites
CPAN: Module::Build loaded ok (v0.280801)
---- Unsatisfied dependencies detected during ----
----       DROLSKY/DateTime-0.51.tar.gz       ----
    Params::Validate [requires]
Skipping test because of notest pragma
Running Build install
  Delayed until after prerequisites
Running install for module 'Params::Validate'
'YAML' not installed, falling back to Data::Dumper and Storable to read prefs '/home/cruggeri/.cpan/prefs'
Running make for D/DR/DROLSKY/Params-Validate-0.94.tar.gz
Checksum for /home/cruggeri/.cpan/source/authors/id/D/DR/DROLSKY/Params-Validate-0.94.tar.gz ok
Params-Validate-0.94
Params-Validate-0.94/META.yml
Params-Validate-0.94/Changes
Params-Validate-0.94/README
Params-Validate-0.94/TODO
Params-Validate-0.94/MANIFEST
Params-Validate-0.94/SIGNATURE
Params-Validate-0.94/LICENSE
Params-Validate-0.94/Build.PL
Params-Validate-0.94/t
Params-Validate-0.94/t/13-taint.t
Params-Validate-0.94/t/09-regex.t
Params-Validate-0.94/t/14-no_validate.t
Params-Validate-0.94/t/03-attribute.t
Params-Validate-0.94/t/18-depends.t
Params-Validate-0.94/t/06-options.t
Params-Validate-0.94/t/04-defaults.t
Params-Validate-0.94/t/25-undef-regex.t
Params-Validate-0.94/t/23-readonly.t
Params-Validate-0.94/t/27-string-as-type.t
Params-Validate-0.94/t/08-noop_with.t
Params-Validate-0.94/t/05-noop_default.t
Params-Validate-0.94/t/pod.t
Params-Validate-0.94/t/21-can.t
Params-Validate-0.94/t/30-hashref-alteration.t
Params-Validate-0.94/t/22-overload-can-bug.t
Params-Validate-0.94/t/15-case.t
Params-Validate-0.94/t/01-validate.t
Params-Validate-0.94/t/10-noop_regex.t
Params-Validate-0.94/t/17-callbacks.t
Params-Validate-0.94/t/19-untaint.t
Params-Validate-0.94/t/29-taint-mode.t
Params-Validate-0.94/t/28-readonly-return.t
Params-Validate-0.94/t/02-noop.t
Params-Validate-0.94/t/pod-coverage.t
Params-Validate-0.94/t/07-with.t
Params-Validate-0.94/t/24-tied.t
Params-Validate-0.94/t/11-cb.t
Params-Validate-0.94/t/16-normalize.t
Params-Validate-0.94/t/12-noop_cb.t
Params-Validate-0.94/t/26-isa.t
Params-Validate-0.94/t/kwalitee.t
Params-Validate-0.94/t/lib
Params-Validate-0.94/t/lib/PVTests.pm
Params-Validate-0.94/t/lib/PVTests
Params-Validate-0.94/t/lib/PVTests/Regex.pm
Params-Validate-0.94/t/lib/PVTests/With.pm
Params-Validate-0.94/t/lib/PVTests/Standard.pm
Params-Validate-0.94/t/lib/PVTests/Callbacks.pm
Params-Validate-0.94/t/lib/PVTests/Defaults.pm
Params-Validate-0.94/benchmarks
Params-Validate-0.94/benchmarks/basic
Params-Validate-0.94/c
Params-Validate-0.94/c/ppport.h
Params-Validate-0.94/lib
Params-Validate-0.94/lib/Params
Params-Validate-0.94/lib/Params/ValidateXS.pm
Params-Validate-0.94/lib/Params/Validate.pm
Params-Validate-0.94/lib/Params/Validate.xs
Params-Validate-0.94/lib/Params/ValidatePP.pm
Params-Validate-0.94/lib/Attribute
Params-Validate-0.94/lib/Attribute/Params
Params-Validate-0.94/lib/Attribute/Params/Validate.pm
Warning (usually harmless): 'YAML' not installed, will not store persistent state

  CPAN.pm: Going to build D/DR/DROLSKY/Params-Validate-0.94.tar.gz

Checking whether your kit is complete...
Looks good

Checking prerequisites...
Looks good

Creating new 'Build' script for 'Params-Validate' version '0.94'
Could not read '/home/cruggeri/.cpan/build/Params-Validate-0.94-uxpzQF/META.yml'. Falling back to other methods to determine prerequisites
Copying lib/Attribute/Params/Validate.pm -> blib/lib/Attribute/Params/Validate.pm
Copying lib/Params/ValidatePP.pm -> blib/lib/Params/ValidatePP.pm
Copying lib/Params/Validate.pm -> blib/lib/Params/Validate.pm
Copying lib/Params/ValidateXS.pm -> blib/lib/Params/ValidateXS.pm
lib/Params/Validate.xs -> lib/Params/Validate.c
cc -Ic -I/usr/lib/perl/5.10/CORE -DXS_VERSION="0.94" -DVERSION="0.94" -fPIC -c -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g -o lib/Params/Validate.o lib/Params/Validate.c
  DROLSKY/Params-Validate-0.94.tar.gz
  ./Build --install_base "/usr/local/bugzilla-3.4.2/lib" -- NOT OK
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Skipping test because of notest pragma
Running Build install
  Make had returned bad status, install seems impossible
Running Build for D/DR/DROLSKY/DateTime-0.51.tar.gz
  Has already been unwrapped into directory /home/cruggeri/.cpan/build/DateTime-0.51-19Gkau

  CPAN.pm: Going to build D/DR/DROLSKY/DateTime-0.51.tar.gz

Warning: Prerequisite 'Params::Validate => 0.76' for 'D/DR/DROLSKY/DateTime-0.51.tar.gz' failed when processing 'D/DR/DROLSKY/Params-Validate-0.94.tar.gz' with 'make => NO'. Continuing, but chances to succeed are limited.
Copying lib/DateTime.pm -> blib/lib/DateTime.pm
Copying lib/DateTime/Helpers.pm -> blib/lib/DateTime/Helpers.pm
Copying lib/DateTime/Duration.pm -> blib/lib/DateTime/Duration.pm
Copying lib/DateTimePP.pm -> blib/lib/DateTimePP.pm
Copying lib/DateTimePPExtra.pm -> blib/lib/DateTimePPExtra.pm
Copying lib/DateTime/Infinite.pm -> blib/lib/DateTime/Infinite.pm
Copying lib/DateTime/LeapSecond.pm -> blib/lib/DateTime/LeapSecond.pm
lib/DateTime.xs -> lib/DateTime.c
cc -Ic -I/usr/lib/perl/5.10/CORE -DXS_VERSION="0.51" -DVERSION="0.51" -fPIC -c -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g -o lib/DateTime.o lib/DateTime.c
  DROLSKY/DateTime-0.51.tar.gz
  ./Build --install_base "/usr/local/bugzilla-3.4.2/lib" -- NOT OK
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Skipping test because of notest pragma
Running Build install
  Make had returned bad status, install seems impossible

```

If somebody can help me, it is very appreciated!

thanks in advance!

---

### Post by daveysan on 2009-12-22
Hi. I had a similar issue and the issue was that I needed mysql dev tools installed. If this sounds like it may be toyr problem then try the following

sudo apt-get install libmysql++-dev

Good luck

---

### Post by norivallyy on 2010-04-01
I think you need to install libyaml-perl


sudo apt-get install libyaml-perl

---

### Post by E.Hyde on 2010-04-01
I forget to mark this thread as solved.
In that case the problem was fix the write permission on the bugzilla folder..

---

### Post by rathna on 2010-06-11
What permissions did you give? Can y ou explain?? I"m having this problem too.

---

### Post by rathna on 2010-06-11
Ha, I just needed a c compiler. The following did the trick

$ sudo apt-get update
$ sudo apt-get install build-essential

---

