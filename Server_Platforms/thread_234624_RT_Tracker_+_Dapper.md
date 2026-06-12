---
title: "RT Tracker + Dapper"
date: 2006-08-11
forum: Server Platforms
---

### Post by Ozz on 2006-08-11
Hello, I'm attempting an install and I got stuck on perl dependancies while trying to run cpan install Apache::Session
It goes nowhere...
Here is some info:
```

  CPAN.pm: Going to build J/JU/JUNOS/junoscript-perl-6.4I0.tar.gz

Checking if your kit is complete...
Looks good
Warning: prerequisite Date::Manip 0 not found.
Warning: prerequisite IO::Tty 0 not found.
Warning: prerequisite Parse::Yapp::Driver 0 not found.
Warning: prerequisite XML::DOM 0 not found.
Warning: prerequisite XML::Parser::PerlSAX 0 not found.
Writing Makefile for junoscript-perl
---- Unsatisfied dependencies detected during [J/JU/JUNOS/junoscript-perl-6.4I0.tar.gz] -----
    IO::Tty
    XML::DOM
    XML::Parser::PerlSAX
    Date::Manip
    Parse::Yapp::Driver
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes]

<snip>-----------------------------------------------------

  CPAN.pm: Going to build T/TJ/TJMATHER/XML-DOM-1.44.tar.gz

Checking if your kit is complete...
Looks good
Warning: prerequisite XML::Parser::PerlSAX 0.07 not found.
Warning: prerequisite XML::RegExp 0 not found.
Writing Makefile for XML-DOM
---- Unsatisfied dependencies detected during [T/TJ/TJMATHER/XML-DOM-1.44.tar.gz] -----
    XML::Parser::PerlSAX
    XML::RegExp
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes]

<snip>-----------------------------------------------------------

  CPAN.pm: Going to build C/CW/CWEST/Apache-Session-1.81.tar.gz

Checking if your kit is complete...
Looks good
Warning: prerequisite Test::Deep 0.082 not found.
Warning: prerequisite Test::Exception 0.15 not found.
Writing Makefile for Apache::Session
---- Unsatisfied dependencies detected during [C/CW/CWEST/Apache-Session-1.81.tar.gz] -----
    Test::Exception
    Test::Deep
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes]
<snip>-----------------------------------------------------------
  
  CPAN.pm: Going to build A/AD/ADIE/Test-Exception-0.21.tar.gz

Checking if your kit is complete...
Looks good
Warning: prerequisite Sub::Uplevel 0.06 not found.
Warning: prerequisite Test::Builder::Tester 1.01 not found.
Writing Makefile for Test::Exception
---- Unsatisfied dependencies detected during [A/AD/ADIE/Test-Exception-0.21.tar.gz] -----
    Sub::Uplevel
    Test::Builder::Tester
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes]

<snip>-----------------------------------------------------------
  
  CPAN.pm: Going to build F/FD/FDALY/Test-Deep-0.095.tar.gz

Checking if your kit is complete...
Looks good
Warning: prerequisite Test::NoWarnings 0.02 not found.
Warning: prerequisite Test::Tester 0.04 not found.
Writing Makefile for Test::Deep
---- Unsatisfied dependencies detected during [F/FD/FDALY/Test-Deep-0.095.tar.gz] -----
    Test::Tester
    Test::NoWarnings
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes]

<snip>-----------------------------------------------------------
  CPAN.pm: Going to build F/FD/FDALY/Test-NoWarnings-0.082.tar.gz

Checking if your kit is complete...
Looks good
Warning: prerequisite Test::Tester 0.103 not found.
Writing Makefile for Test::NoWarnings
---- Unsatisfied dependencies detected during [F/FD/FDALY/Test-NoWarnings-0.082.tar.gz] -----
    Test::Tester
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes]

```

Hope it's not too big a chunk to post here...

Thanks in advance to any help,

Ozz.

---

### Post by Ozz on 2006-08-12
****bump****

If this is not ok please let me know!


Ozz.

---

### Post by Ozz on 2006-08-13
Well in the original post I missed aome info @ the end of the cpan install Apache::Session ](*,) 

Here it is```

  CPAN.pm: Going to build G/GE/GEOFF/Apache-Test-1.28.tar.gz

[   info] generating script t/TEST
[   info] generating script ./t/cgi-bin/cookies.pl
[   info] generating script ./t/cgi-bin/next_available_port.pl
Checking if your kit is complete...
Looks good
Writing Makefile for Apache::Test
Checking for File::Spec...ok
Checking for Cwd...ok
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
root@it002:~#

```

Thank you,

Ozz.

---

### Post by Ozz on 2006-08-14
Continuing with my monologue.... ;) 

Apparently I can download all missing modules [here](http://www.cpan.org/modules/01modules.index.html).

Ozz.

---

### Post by Hezekiah on 2006-08-14
It's hard to tell due to the snipped data copied and pasted in, but do you have the build-essential Ubuntu package installed?  If so (or, even if not...) there should be a block of error messages somewhere in the output.  They may offer more detailed assistance, either for you or for posting here.

Good luck either way though.

---

### Post by Ozz on 2006-08-14
First of all, many thanks for the reply... :D 

[quote="Hezekiah"]but do you have the build-essential Ubuntu package installed? [/quote]

Sorry, I'm not too sure about that.... (noob in Ubuntu)could you drop me a link to this package? I'll be searching for it.

I did try to keep the data snippets short or I'd take a lot of space here and I'm not familiar with the forum...

As for the error messages I for some time had the deer-in-the-headlights syndrome but after having a weekend to deal with it I found @ cpan a page where I can download all the missing modules.

If there's a single package that would make my life easier than I'll thank much the kind soul that points me in the right direction.... ;) 

EDIT: I found and installed the build-essential and made no difference, to the results here. Will look at individual packages.


Best regards,

Ozz.

---

### Post by Hezekiah on 2006-08-14
How are you installing RT?  I haven't done the installation before, but from the output you pasted it looks like it uses the cpan shell, or something similar, to install its dependencies.  If you are comfortable with cpan, it may be worth installing the dependencies through there.  The easiest way (but not really the safest, since the packages are installed system-wide and everything is done as root):

```

sudo su -
cpan

```
then, after configuring cpan:
```

install Some::Package::You::Need

```

I install a lot of modules on my system this way because I do a lot of development work in Perl.

Another possible approach is to install the request-tracker3.4 package available in the Ubuntu Universe repository.  It's an older version than the latest available from bestpractical.com, but it should pull in all of the dependencies you'll need as Debian/Ubuntu packages.
```

sudo apt-get install request-tracker3.4

```

I apologize if you know any/all of this already.  But, sadly, Perl is a second class citizen in Ubuntu so things aren't always as easy as they could be.

---

### Post by Ozz on 2006-08-14
[quote="Hezekiah"]I apologize if you know any/all of this already. But, sadly, Perl is a second class citizen in Ubuntu so things aren't always as easy as they could be.[/quote]

Please don't! That has been of great help.
I was about to download manually with wget all the missing cpan modules.... ;) 

Ozz.

---

### Post by Hezekiah on 2006-08-14
I'm glad the information was helpful.   Please post again if you have any further questions.

---

### Post by Ozz on 2006-08-14
I sure will and I do have a few issues here as I attempted the installs and got nowhere.
I will post the full message here.

```
root@it002:~# cpan install Apache::Session
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Sat, 12 Aug 2006 18:31:58 GMT
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  ftp://CPAN.mirror.rafal.ca/pub/CPAN/authors/01mailrc.txt.gz
LWP failed with code[404] message[File '01mailrc.txt.gz' not found]
Fetching with Net::FTP:
  ftp://CPAN.mirror.rafal.ca/pub/CPAN/authors/01mailrc.txt.gz
Couldn't fetch 01mailrc.txt.gz from CPAN.mirror.rafal.ca
Fetching with LWP:
  ftp://cpan.sunsite.ualberta.ca/pub/CPAN/authors/01mailrc.txt.gz
LWP failed with code[404] message[File '01mailrc.txt.gz' not found]
Fetching with Net::FTP:
  ftp://cpan.sunsite.ualberta.ca/pub/CPAN/authors/01mailrc.txt.gz
Couldn't fetch 01mailrc.txt.gz from cpan.sunsite.ualberta.ca
Fetching with LWP:
  ftp://ftp.nrc.ca/pub/CPAN/authors/01mailrc.txt.gz
LWP failed with code[404] message[File '01mailrc.txt.gz' not found]
Fetching with Net::FTP:
  ftp://ftp.nrc.ca/pub/CPAN/authors/01mailrc.txt.gz
Couldn't fetch 01mailrc.txt.gz from ftp.nrc.ca

Trying with "/usr/bin/lynx -source" to get
    ftp://CPAN.mirror.rafal.ca/pub/CPAN/authors/01mailrc.txt.gz
CPAN: Compress::Zlib loaded ok
Going to read /root/.cpan/sources/authors/01mailrc.txt.gz

Trying with "/usr/bin/lynx -source" to get
    ftp://CPAN.mirror.rafal.ca/pub/CPAN/modules/02packages.details.txt.gz
Going to read /root/.cpan/sources/modules/02packages.details.txt.gz
  Database was generated on Sun, 13 Aug 2006 19:29:57 GMT

  There's a new CPAN.pm version (v1.87) available!
  [Current version is v1.7601]
  You might want to try
    install Bundle::CPAN
    reload cpan
  without quitting the current session. It should be a seamless upgrade
  while we are running...


Trying with "/usr/bin/lynx -source" to get
    ftp://CPAN.mirror.rafal.ca/pub/CPAN/modules/03modlist.data.gz
Going to read /root/.cpan/sources/modules/03modlist.data.gz
Going to write /root/.cpan/Metadata
Running install for module install
Running make for J/JU/JUNOS/junoscript-perl-6.4I0.tar.gz
CPAN: Digest::MD5 loaded ok
Checksum for /root/.cpan/sources/authors/id/J/JU/JUNOS/junoscript-perl-6.4I0.tar.gz ok
Scanning cache /root/.cpan/build for sizes
junoscript-perl-6.4I0/
junoscript-perl-6.4I0/lib/
junoscript-perl-6.4I0/lib/JUNOS/
junoscript-perl-6.4I0/lib/JUNOS/Access/
junoscript-perl-6.4I0/lib/JUNOS/Access/stubs.pm
junoscript-perl-6.4I0/lib/JUNOS/Access/clear_text.pm
junoscript-perl-6.4I0/lib/JUNOS/Access/ssh.pm
junoscript-perl-6.4I0/lib/JUNOS/Access/ssl.pm
junoscript-perl-6.4I0/lib/JUNOS/Access/xnm.pm
junoscript-perl-6.4I0/lib/JUNOS/Access/telnet.pm
junoscript-perl-6.4I0/lib/JUNOS/Access/rsh.pm
junoscript-perl-6.4I0/lib/JUNOS/Access.pm
junoscript-perl-6.4I0/lib/JUNOS/Methods.pm
junoscript-perl-6.4I0/lib/JUNOS/DOM/
junoscript-perl-6.4I0/lib/JUNOS/DOM/Parser.pm
junoscript-perl-6.4I0/lib/JUNOS/6.4I0/
junoscript-perl-6.4I0/lib/JUNOS/6.4I0/jkernel_methods.pl
junoscript-perl-6.4I0/lib/JUNOS/6.4I0/jroute_methods.pl
junoscript-perl-6.4I0/lib/JUNOS/6.4I0/jcrypto_methods.pl
junoscript-perl-6.4I0/lib/JUNOS/Response.pm
junoscript-perl-6.4I0/lib/JUNOS/version.pm
junoscript-perl-6.4I0/lib/JUNOS/Trace.pm
junoscript-perl-6.4I0/lib/JUNOS/Device.pm
junoscript-perl-6.4I0/examples/
junoscript-perl-6.4I0/examples/get_chassis_inventory/
junoscript-perl-6.4I0/examples/get_chassis_inventory/banner_logo.gif
junoscript-perl-6.4I0/examples/get_chassis_inventory/xsl/
junoscript-perl-6.4I0/examples/get_chassis_inventory/xsl/chassis_inventory_csv.xsl
junoscript-perl-6.4I0/examples/get_chassis_inventory/xsl/chassis_inventory_xml.xsl
junoscript-perl-6.4I0/examples/get_chassis_inventory/xsl/chassis_inventory_html.xsl
junoscript-perl-6.4I0/examples/get_chassis_inventory/get_chassis_inventory.pl
junoscript-perl-6.4I0/examples/RDB/
junoscript-perl-6.4I0/examples/RDB/README
junoscript-perl-6.4I0/examples/RDB/common.pm
junoscript-perl-6.4I0/examples/RDB/unpop_tables.pl
junoscript-perl-6.4I0/examples/RDB/get_config.pl
junoscript-perl-6.4I0/examples/RDB/pop_tables.pl
junoscript-perl-6.4I0/examples/RDB/make_tables.pl
junoscript-perl-6.4I0/examples/load_configuration/
junoscript-perl-6.4I0/examples/load_configuration/requests/
junoscript-perl-6.4I0/examples/load_configuration/requests/set_login_user_foo.xml
junoscript-perl-6.4I0/examples/load_configuration/requests/set_login_class_bar.xml
junoscript-perl-6.4I0/examples/load_configuration/load_configuration.pl
junoscript-perl-6.4I0/examples/diagnose_bgp/
junoscript-perl-6.4I0/examples/diagnose_bgp/js/
junoscript-perl-6.4I0/examples/diagnose_bgp/js/sorttable.js
junoscript-perl-6.4I0/examples/diagnose_bgp/xsl/
junoscript-perl-6.4I0/examples/diagnose_bgp/xsl/text.xsl
junoscript-perl-6.4I0/examples/diagnose_bgp/xsl/html.xsl
junoscript-perl-6.4I0/examples/diagnose_bgp/xsl/dhtml.xsl
junoscript-perl-6.4I0/examples/diagnose_bgp/diagnose_bgp.pl
junoscript-perl-6.4I0/banner_logo.gif
junoscript-perl-6.4I0/MANIFEST
junoscript-perl-6.4I0/CHANGES
junoscript-perl-6.4I0/to_topg.gif
junoscript-perl-6.4I0/install.pm
junoscript-perl-6.4I0/Makefile.PL
junoscript-perl-6.4I0/README
junoscript-perl-6.4I0/install-prereqs.pl
junoscript-perl-6.4I0/README.html
junoscript-perl-6.4I0/required-mod.pl
junoscript-perl-6.4I0/access/
junoscript-perl-6.4I0/access/ssh.pm
junoscript-perl-6.4I0/access/ssl.pm
junoscript-perl-6.4I0/t/
junoscript-perl-6.4I0/t/base-1.t
junoscript-perl-6.4I0/t/base-2.t
Removing previously used /root/.cpan/build/junoscript-perl-6.4I0

  CPAN.pm: Going to build J/JU/JUNOS/junoscript-perl-6.4I0.tar.gz

Checking if your kit is complete...
Looks good
Warning: prerequisite Date::Manip 0 not found.
Warning: prerequisite IO::Tty 0 not found.
Warning: prerequisite Parse::Yapp::Driver 0 not found.
Warning: prerequisite XML::DOM 0 not found.
Warning: prerequisite XML::Parser::PerlSAX 0 not found.
Writing Makefile for junoscript-perl
---- Unsatisfied dependencies detected during [J/JU/JUNOS/junoscript-perl-6.4I0.tar.gz] -----
    IO::Tty
    XML::DOM
    XML::Parser::PerlSAX
    Date::Manip
    Parse::Yapp::Driver
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes]

Running install for module XML::RegExp
Running make for T/TJ/TJMATHER/XML-RegExp-0.03.tar.gz
Checksum for /root/.cpan/sources/authors/id/T/TJ/TJMATHER/XML-RegExp-0.03.tar.gz ok
XML-RegExp-0.03/
XML-RegExp-0.03/Changes
XML-RegExp-0.03/MANIFEST
XML-RegExp-0.03/Makefile.PL
XML-RegExp-0.03/README
XML-RegExp-0.03/test.pl
XML-RegExp-0.03/lib/
XML-RegExp-0.03/lib/XML/
XML-RegExp-0.03/lib/XML/RegExp.pm
Removing previously used /root/.cpan/build/XML-RegExp-0.03

  CPAN.pm: Going to build T/TJ/TJMATHER/XML-RegExp-0.03.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for XML::RegExp
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running make for T/TJ/TJMATHER/XML-DOM-1.44.tar.gz
  Is already unwrapped into directory /root/.cpan/build/XML-DOM-1.44

  CPAN.pm: Going to build T/TJ/TJMATHER/XML-DOM-1.44.tar.gz

    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running install for module XML::Parser::PerlSAX
Running make for K/KM/KMACLEOD/libxml-perl-0.08.tar.gz
  Is already unwrapped into directory /root/.cpan/build/libxml-perl-0.08
  Has already been processed within this session
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running install for module Date::Manip
Running make for S/SB/SBECK/DateManip-5.44.tar.gz
Checksum for /root/.cpan/sources/authors/id/S/SB/SBECK/DateManip-5.44.tar.gz ok
DateManip-5.44/
DateManip-5.44/t/
DateManip-5.44/t/Manip.cnf
DateManip-5.44/t/convtz.t
DateManip-5.44/t/date.t
DateManip-5.44/t/date_date_0.t
DateManip-5.44/t/date_date_1.t
DateManip-5.44/t/date_date_2a.t
DateManip-5.44/t/date_date_2b.t
DateManip-5.44/t/date_delta_0.t
DateManip-5.44/t/date_delta_1.t
DateManip-5.44/t/date_delta_2a.t
DateManip-5.44/t/date_delta_2b.t
DateManip-5.44/t/date_delta_french.t
DateManip-5.44/t/date_delta_russian.t
DateManip-5.44/t/date_delta_sign.t
DateManip-5.44/t/date_french.t
DateManip-5.44/t/date_german.t
DateManip-5.44/t/date_misc_a.t
DateManip-5.44/t/date_misc_b.t
DateManip-5.44/t/date_romanian.t
DateManip-5.44/t/date_russian.t
DateManip-5.44/t/date_today_0.t
DateManip-5.44/t/date_today_1.t
DateManip-5.44/t/delta_a.t
DateManip-5.44/t/delta_b.t
DateManip-5.44/t/delta_delta_0.t
DateManip-5.44/t/delta_delta_1.t
DateManip-5.44/t/delta_delta_2a.t
DateManip-5.44/t/delta_delta_2b.t
DateManip-5.44/t/delta_format.t
DateManip-5.44/t/delta_romanian.t
DateManip-5.44/t/events.t
DateManip-5.44/t/getnext.t
DateManip-5.44/t/getprev.t
DateManip-5.44/t/nthday.t
DateManip-5.44/t/recur_0.t
DateManip-5.44/t/recur_1.t
DateManip-5.44/t/runtests
DateManip-5.44/t/runtests.bat
DateManip-5.44/t/settime.t
DateManip-5.44/t/test.pl
DateManip-5.44/t/unixdate.t
DateManip-5.44/Manip.pm
DateManip-5.44/DateManip.cnf
DateManip-5.44/HISTORY
DateManip-5.44/INSTALL
DateManip-5.44/MANIFEST
DateManip-5.44/Makefile.PL
DateManip-5.44/Makefile.old
DateManip-5.44/Manip.pod
DateManip-5.44/README
DateManip-5.44/TODO
Removing previously used /root/.cpan/build/DateManip-5.44

  CPAN.pm: Going to build S/SB/SBECK/DateManip-5.44.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for Date::Manip
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running install for module Parse::Yapp::Driver
Running make for F/FD/FDESAR/Parse-Yapp-1.05.tar.gz
Checksum for /root/.cpan/sources/authors/id/F/FD/FDESAR/Parse-Yapp-1.05.tar.gz ok
Parse-Yapp-1.05/
Parse-Yapp-1.05/README
Parse-Yapp-1.05/Calc.yp
Parse-Yapp-1.05/MANIFEST
Parse-Yapp-1.05/yapp
Parse-Yapp-1.05/lib/
Parse-Yapp-1.05/lib/Parse/
Parse-Yapp-1.05/lib/Parse/Yapp/
Parse-Yapp-1.05/lib/Parse/Yapp/Output.pm
Parse-Yapp-1.05/lib/Parse/Yapp/Driver.pm
Parse-Yapp-1.05/lib/Parse/Yapp/Grammar.pm
Parse-Yapp-1.05/lib/Parse/Yapp/Lalr.pm
Parse-Yapp-1.05/lib/Parse/Yapp/Parse.pm
Parse-Yapp-1.05/lib/Parse/Yapp/Options.pm
Parse-Yapp-1.05/lib/Parse/Yapp.pm
Parse-Yapp-1.05/Changes
Parse-Yapp-1.05/Makefile.PL
Parse-Yapp-1.05/t/
Parse-Yapp-1.05/t/stress.t
Parse-Yapp-1.05/t/base.t
Parse-Yapp-1.05/t/calc.t
Parse-Yapp-1.05/YappParse.yp
Removing previously used /root/.cpan/build/Parse-Yapp-1.05

  CPAN.pm: Going to build F/FD/FDESAR/Parse-Yapp-1.05.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for Parse::Yapp
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running make for J/JU/JUNOS/junoscript-perl-6.4I0.tar.gz
  Is already unwrapped into directory /root/.cpan/build/junoscript-perl-6.4I0

  CPAN.pm: Going to build J/JU/JUNOS/junoscript-perl-6.4I0.tar.gz

    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running install for module Apache::Session
Running make for C/CW/CWEST/Apache-Session-1.81.tar.gz
Checksum for /root/.cpan/sources/authors/id/C/CW/CWEST/Apache-Session-1.81.tar.gz ok
Apache-Session-1.81/
Apache-Session-1.81/b/
Apache-Session-1.81/b/dbi.b
Apache-Session-1.81/b/dbinew.b
Apache-Session-1.81/b/dbipop.b
Apache-Session-1.81/b/dbstore.b
Apache-Session-1.81/b/flexpop.b
Apache-Session-1.81/b/gdbm.b
Apache-Session-1.81/b/mysqllock.b
Apache-Session-1.81/b/uuevsmime.b
Apache-Session-1.81/CHANGES
Apache-Session-1.81/eg/
Apache-Session-1.81/eg/example.perl
Apache-Session-1.81/INSTALL
Apache-Session-1.81/Makefile.PL
Apache-Session-1.81/MANIFEST
Apache-Session-1.81/META.yml
Apache-Session-1.81/README
Apache-Session-1.81/Session/
Apache-Session-1.81/Session/DB_File.pm
Apache-Session-1.81/Session/File.pm
Apache-Session-1.81/Session/Flex.pm
Apache-Session-1.81/Session/Generate/
Apache-Session-1.81/Session/Generate/MD5.pm
Apache-Session-1.81/Session/Generate/ModUniqueId.pm
Apache-Session-1.81/Session/Generate/ModUsertrack.pm
Apache-Session-1.81/Session/Informix.pm
Apache-Session-1.81/Session/Lock/
Apache-Session-1.81/Session/Lock/File.pm
Apache-Session-1.81/Session/Lock/MySQL.pm
Apache-Session-1.81/Session/Lock/Null.pm
Apache-Session-1.81/Session/Lock/Semaphore.pm
Apache-Session-1.81/Session/Lock/Sybase.pm
Apache-Session-1.81/Session/MySQL.pm
Apache-Session-1.81/Session/Oracle.pm
Apache-Session-1.81/Session/Postgres.pm
Apache-Session-1.81/Session/Serialize/
Apache-Session-1.81/Session/Serialize/Base64.pm
Apache-Session-1.81/Session/Serialize/Storable.pm
Apache-Session-1.81/Session/Serialize/Sybase.pm
Apache-Session-1.81/Session/Serialize/UUEncode.pm
Apache-Session-1.81/Session/Store/
Apache-Session-1.81/Session/Store/DB_File.pm
Apache-Session-1.81/Session/Store/DBI.pm
Apache-Session-1.81/Session/Store/File.pm
Apache-Session-1.81/Session/Store/Informix.pm
Apache-Session-1.81/Session/Store/MySQL.pm
Apache-Session-1.81/Session/Store/Oracle.pm
Apache-Session-1.81/Session/Store/Postgres.pm
Apache-Session-1.81/Session/Store/Sybase.pm
Apache-Session-1.81/Session/Sybase.pm
Apache-Session-1.81/Session.pm
Apache-Session-1.81/t/
Apache-Session-1.81/t/99base64.t
Apache-Session-1.81/t/99dbfile.t
Apache-Session-1.81/t/99dbfilestore.t
Apache-Session-1.81/t/99file.t
Apache-Session-1.81/t/99filelock.t
Apache-Session-1.81/t/99filestore.t
Apache-Session-1.81/t/99flex.t
Apache-Session-1.81/t/99md5gen.t
Apache-Session-1.81/t/99moduniqgen.t
Apache-Session-1.81/t/99mysql.t
Apache-Session-1.81/t/99mysqllock.t
Apache-Session-1.81/t/99mysqlstore.t
Apache-Session-1.81/t/99nulllock.t
Apache-Session-1.81/t/99oracle.t
Apache-Session-1.81/t/99postgres.t
Apache-Session-1.81/t/99semaphore.t
Apache-Session-1.81/t/99storable.t
Apache-Session-1.81/t/99uue.t
Apache-Session-1.81/TODO
Removing previously used /root/.cpan/build/Apache-Session-1.81

  CPAN.pm: Going to build C/CW/CWEST/Apache-Session-1.81.tar.gz

Checking if your kit is complete...
Looks good
Warning: prerequisite Test::Deep 0.082 not found.
Warning: prerequisite Test::Exception 0.15 not found.
Writing Makefile for Apache::Session
---- Unsatisfied dependencies detected during [C/CW/CWEST/Apache-Session-1.81.tar.gz] -----
    Test::Exception
    Test::Deep
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes]

```
Had to cut it halfway, too big says the forum...  :oops: 

Well there is as much as I could retrieve.
Thanks once more for all your help.

Ozz.

---

### Post by Ozz on 2006-08-14
Here is the rest
```

Running make test
  Delayed until after prerequisites
Running make install
  Delayed until after prerequisites
Running install for module Test::Exception
Running make for A/AD/ADIE/Test-Exception-0.21.tar.gz
Checksum for /root/.cpan/sources/authors/id/A/AD/ADIE/Test-Exception-0.21.tar.gz ok
Test-Exception-0.21/
Test-Exception-0.21/Build.PL
Test-Exception-0.21/Changes
Test-Exception-0.21/lib/
Test-Exception-0.21/lib/Test/
Test-Exception-0.21/lib/Test/Exception.pm
Test-Exception-0.21/Makefile.PL
Test-Exception-0.21/MANIFEST
Test-Exception-0.21/META.yml
Test-Exception-0.21/README
Test-Exception-0.21/SIGNATURE
Test-Exception-0.21/t/
Test-Exception-0.21/t/caller.t
Test-Exception-0.21/t/documented.t
Test-Exception-0.21/t/Exception.t
Test-Exception-0.21/t/lives_and.t
Test-Exception-0.21/t/pod.t
Test-Exception-0.21/t/preserve.t
Test-Exception-0.21/t/return.t
Test-Exception-0.21/t/stacktrace.t
Removing previously used /root/.cpan/build/Test-Exception-0.21

  CPAN.pm: Going to build A/AD/ADIE/Test-Exception-0.21.tar.gz

Checking if your kit is complete...
Looks good
Warning: prerequisite Sub::Uplevel 0.06 not found.
Warning: prerequisite Test::Builder::Tester 1.01 not found.
Writing Makefile for Test::Exception
---- Unsatisfied dependencies detected during [A/AD/ADIE/Test-Exception-0.21.tar.gz] -----
    Sub::Uplevel
    Test::Builder::Tester
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes]

Sub-Uplevel-0.13/Makefile.PL
Removing previously used /root/.cpan/build/Sub-Uplevel-0.13

  CPAN.pm: Going to build D/DA/DAGOLDEN/Sub-Uplevel-0.13.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for Sub::Uplevel
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running install for module Test::Builder::Tester
Running make for M/MS/MSCHWERN/Test-Simple-0.64.tar.gz
Checksum for /root/.cpan/sources/authors/id/M/MS/MSCHWERN/Test-Simple-0.64.tar.gz ok
Test-Simple-0.64/
Test-Simple-0.64/Changes
Test-Simple-0.64/lib/
Test-Simple-0.64/lib/Test/
Test-Simple-0.64/lib/Test/Builder/
Test-Simple-0.64/lib/Test/Builder/Module.pm
Test-Simple-0.64/lib/Test/Builder/Tester/
Test-Simple-0.64/lib/Test/Builder/Tester/Color.pm
Test-Simple-0.64/lib/Test/Builder/Tester.pm
Test-Simple-0.64/lib/Test/Builder.pm
Test-Simple-0.64/lib/Test/More.pm
Test-Simple-0.64/lib/Test/Simple.pm
Test-Simple-0.64/lib/Test/Tutorial.pod
Test-Simple-0.64/Makefile.PL
Test-Simple-0.64/MANIFEST
Test-Simple-0.64/META.yml
Test-Simple-0.64/README
Test-Simple-0.64/t/
Test-Simple-0.64/t/00signature.t
Test-Simple-0.64/t/00test_harness_check.t
Test-Simple-0.64/t/bad_plan.t
Test-Simple-0.64/t/bail_out.t
Test-Simple-0.64/t/buffer.t
Test-Simple-0.64/t/Builder.t
Test-Simple-0.64/t/circular_data.t
Test-Simple-0.64/t/create.t
Test-Simple-0.64/t/curr_test.t
Test-Simple-0.64/t/details.t
Test-Simple-0.64/t/diag.t
Test-Simple-0.64/t/eq_set.t
Test-Simple-0.64/t/exit.t
Test-Simple-0.64/t/extra.t
Test-Simple-0.64/t/extra_one.t
Test-Simple-0.64/t/fail-like.t
Test-Simple-0.64/t/fail-more.t
Test-Simple-0.64/t/fail.t
Test-Simple-0.64/t/fail_one.t
Test-Simple-0.64/t/filehandles.t
Test-Simple-0.64/t/fork.t
Test-Simple-0.64/t/harness_active.t
Test-Simple-0.64/t/has_plan.t
Test-Simple-0.64/t/has_plan2.t
Test-Simple-0.64/t/import.t
Test-Simple-0.64/t/is_deeply_fail.t
Test-Simple-0.64/t/is_fh.t
Test-Simple-0.64/t/lib/
Test-Simple-0.64/t/lib/NoExporter.pm
Test-Simple-0.64/t/lib/Test/
Test-Simple-0.64/t/lib/Test/Simple/
Test-Simple-0.64/t/lib/Test/Simple/Catch.pm
Test-Simple-0.64/t/lib/Test/Simple/sample_tests/
Test-Simple-0.64/t/lib/Test/Simple/sample_tests/death.plx
Test-Simple-0.64/t/lib/Test/Simple/sample_tests/death_in_eval.plx
Test-Simple-0.64/t/lib/Test/Simple/sample_tests/exit.plx
Test-Simple-0.64/t/lib/Test/Simple/sample_tests/extras.plx
Test-Simple-0.64/t/lib/Test/Simple/sample_tests/five_fail.plx
Test-Simple-0.64/t/lib/Test/Simple/sample_tests/last_minute_death.plx
Test-Simple-0.64/t/lib/Test/Simple/sample_tests/one_fail.plx
Test-Simple-0.64/t/lib/Test/Simple/sample_tests/pre_plan_death.plx
Test-Simple-0.64/t/lib/Test/Simple/sample_tests/require.plx
Test-Simple-0.64/t/lib/Test/Simple/sample_tests/success.plx
Test-Simple-0.64/t/lib/Test/Simple/sample_tests/too_few.plx
Test-Simple-0.64/t/lib/Test/Simple/sample_tests/too_few_fail.plx
Test-Simple-0.64/t/lib/Test/Simple/sample_tests/two_fail.plx
Test-Simple-0.64/t/lib/TieOut.pm
Test-Simple-0.64/t/maybe_regex.t
Test-Simple-0.64/t/missing.t
Test-Simple-0.64/t/More.t
Test-Simple-0.64/t/no_diag.t
Test-Simple-0.64/t/no_ending.t
Test-Simple-0.64/t/no_header.t
Test-Simple-0.64/t/no_plan.t
Test-Simple-0.64/t/ok_obj.t
Test-Simple-0.64/t/output.t
Test-Simple-0.64/t/overload.t
Test-Simple-0.64/t/overload_threads.t
Test-Simple-0.64/t/plan.t
Test-Simple-0.64/t/plan_bad.t
Test-Simple-0.64/t/plan_is_noplan.t
Test-Simple-0.64/t/plan_no_plan.t
Test-Simple-0.64/t/plan_shouldnt_import.t
Test-Simple-0.64/t/plan_skip_all.t
Test-Simple-0.64/t/require_ok.t
Test-Simple-0.64/t/reset.t
Test-Simple-0.64/t/simple.t
Test-Simple-0.64/t/skip.t
Test-Simple-0.64/t/skipall.t
Test-Simple-0.64/t/sort_bug.t
Test-Simple-0.64/t/tbt_01basic.t
Test-Simple-0.64/t/tbt_02fhrestore.t
Test-Simple-0.64/t/tbt_03die.t
Test-Simple-0.64/t/tbt_04line_num.t
Test-Simple-0.64/t/tbt_05faildiag.t
Test-Simple-0.64/t/tbt_06errormess.t
Test-Simple-0.64/t/tbt_07args.t
Test-Simple-0.64/t/thread_taint.t
Test-Simple-0.64/t/threads.t
Test-Simple-0.64/t/todo.t
Test-Simple-0.64/t/undef.t
Test-Simple-0.64/t/use_ok.t
Test-Simple-0.64/t/useing.t
Test-Simple-0.64/TODO
Removing previously used /root/.cpan/build/Test-Simple-0.64

  CPAN.pm: Going to build M/MS/MSCHWERN/Test-Simple-0.64.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for Test::Simple
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running make for A/AD/ADIE/Test-Exception-0.21.tar.gz
  Is already unwrapped into directory /root/.cpan/build/Test-Exception-0.21

  CPAN.pm: Going to build A/AD/ADIE/Test-Exception-0.21.tar.gz

    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running install for module Test::Deep
Running make for F/FD/FDALY/Test-Deep-0.095.tar.gz
Checksum for /root/.cpan/sources/authors/id/F/FD/FDALY/Test-Deep-0.095.tar.gz ok
Test-Deep-0.095/
Test-Deep-0.095/lib/
Test-Deep-0.095/lib/Test/
Test-Deep-0.095/lib/Test/Deep/
Test-Deep-0.095/lib/Test/Deep/Regexp.pm
Test-Deep-0.095/lib/Test/Deep/ArrayLength.pm
Test-Deep-0.095/lib/Test/Deep/ScalarRefOnly.pm
Test-Deep-0.095/lib/Test/Deep/ListMethods.pm
Test-Deep-0.095/lib/Test/Deep/Isa.pm
Test-Deep-0.095/lib/Test/Deep/RegexpRefOnly.pm
Test-Deep-0.095/lib/Test/Deep/RegexpRef.pm
Test-Deep-0.095/lib/Test/Deep/Cache.pm
Test-Deep-0.095/lib/Test/Deep/Any.pm
Test-Deep-0.095/lib/Test/Deep/String.pm
Test-Deep-0.095/lib/Test/Deep/MM.pm
Test-Deep-0.095/lib/Test/Deep/Cmp.pm
Test-Deep-0.095/lib/Test/Deep/Number.pm
Test-Deep-0.095/lib/Test/Deep/HashKeysOnly.pm
Test-Deep-0.095/lib/Test/Deep/Stack.pm
Test-Deep-0.095/lib/Test/Deep/RegexpOnly.pm
Test-Deep-0.095/lib/Test/Deep/HashEach.pm
Test-Deep-0.095/lib/Test/Deep/Code.pm
Test-Deep-0.095/lib/Test/Deep/Boolean.pm
Test-Deep-0.095/lib/Test/Deep/RefType.pm
Test-Deep-0.095/lib/Test/Deep/Array.pm
Test-Deep-0.095/lib/Test/Deep/HashElements.pm
Test-Deep-0.095/lib/Test/Deep/NoTest.pm
Test-Deep-0.095/lib/Test/Deep/Blessed.pm
Test-Deep-0.095/lib/Test/Deep/Class.pm
Test-Deep-0.095/lib/Test/Deep/Ref.pm
Test-Deep-0.095/lib/Test/Deep/Set.pm
Test-Deep-0.095/lib/Test/Deep/All.pm
Test-Deep-0.095/lib/Test/Deep/Ignore.pm
Test-Deep-0.095/lib/Test/Deep/RegexpMatches.pm
Test-Deep-0.095/lib/Test/Deep/Cache/
Test-Deep-0.095/lib/Test/Deep/Cache/Simple.pm
Test-Deep-0.095/lib/Test/Deep/Methods.pm
Test-Deep-0.095/lib/Test/Deep/Shallow.pm
Test-Deep-0.095/lib/Test/Deep/Hash.pm
Test-Deep-0.095/lib/Test/Deep/ArrayLengthOnly.pm
Test-Deep-0.095/lib/Test/Deep/ArrayElementsOnly.pm
Test-Deep-0.095/lib/Test/Deep/ArrayEach.pm
Test-Deep-0.095/lib/Test/Deep/ScalarRef.pm
Test-Deep-0.095/lib/Test/Deep/HashKeys.pm
Test-Deep-0.095/lib/Test/Deep.pod
Test-Deep-0.095/lib/Test/Deep.pm
Test-Deep-0.095/t/
Test-Deep-0.095/t/regexpref.t
Test-Deep-0.095/t/array.t
Test-Deep-0.095/t/scalarref.t
Test-Deep-0.095/t/code.t
Test-Deep-0.095/t/set.t
Test-Deep-0.095/t/reftype.t
Test-Deep-0.095/t/blessed.t
Test-Deep-0.095/t/any.t
Test-Deep-0.095/t/shallow.t
Test-Deep-0.095/t/deep_utils.t
Test-Deep-0.095/t/arraylength.t
Test-Deep-0.095/t/circular.t
Test-Deep-0.095/t/hash_each.t
Test-Deep-0.095/t/listmethods.t
Test-Deep-0.095/t/std.pm
Test-Deep-0.095/t/bag.t
Test-Deep-0.095/t/error.t
Test-Deep-0.095/t/regexp.t.orig
Test-Deep-0.095/t/ignore.t
Test-Deep-0.095/t/cache.t
Test-Deep-0.095/t/hashkeys.t
Test-Deep-0.095/t/notest.t
Test-Deep-0.095/t/class.t
Test-Deep-0.095/t/descend.t
Test-Deep-0.095/t/methods.t
Test-Deep-0.095/t/boolean.t
Test-Deep-0.095/t/string.t
Test-Deep-0.095/t/all.t
Test-Deep-0.095/t/regexp.t
Test-Deep-0.095/t/bagrecursion.t
Test-Deep-0.095/t/isa.t
Test-Deep-0.095/t/scalar.t
Test-Deep-0.095/t/over.pm
Test-Deep-0.095/t/hash.t
Test-Deep-0.095/t/number.t
Test-Deep-0.095/t/array_each.t
Test-Deep-0.095/MANIFEST
Test-Deep-0.095/TODO
Test-Deep-0.095/README
Test-Deep-0.095/CHANGES
Test-Deep-0.095/META.yml
Test-Deep-0.095/Makefile.PL
Removing previously used /root/.cpan/build/Test-Deep-0.095

  CPAN.pm: Going to build F/FD/FDALY/Test-Deep-0.095.tar.gz

Checking if your kit is complete...
Looks good
Warning: prerequisite Test::NoWarnings 0.02 not found.
Warning: prerequisite Test::Tester 0.04 not found.
Writing Makefile for Test::Deep
---- Unsatisfied dependencies detected during [F/FD/FDALY/Test-Deep-0.095.tar.gz] -----
    Test::Tester
    Test::NoWarnings
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes]

Running make test
  Delayed until after prerequisites
Running make install
  Delayed until after prerequisites
Running install for module Test::Tester
Running make for F/FD/FDALY/Test-Tester-0.103.tar.gz
Checksum for /root/.cpan/sources/authors/id/F/FD/FDALY/Test-Tester-0.103.tar.gz ok
Test-Tester-0.103/
Test-Tester-0.103/Makefile.PL
Test-Tester-0.103/META.yml
Test-Tester-0.103/t/
Test-Tester-0.103/t/fail/
Test-Tester-0.103/t/fail/fail.t
Test-Tester-0.103/t/MyTest.pm
Test-Tester-0.103/t/run_test.t
Test-Tester-0.103/t/capture.t
Test-Tester-0.103/t/auto.t
Test-Tester-0.103/t/check_tests.t
Test-Tester-0.103/t/SmallTest.pm
Test-Tester-0.103/t/depth.t
Test-Tester-0.103/CHANGES
Test-Tester-0.103/README
Test-Tester-0.103/lib/
Test-Tester-0.103/lib/Test/
Test-Tester-0.103/lib/Test/Tester/
Test-Tester-0.103/lib/Test/Tester/CaptureRunner.pm
Test-Tester-0.103/lib/Test/Tester/Delegate.pm
Test-Tester-0.103/lib/Test/Tester/Capture.pm
Test-Tester-0.103/lib/Test/Tester.pm
Test-Tester-0.103/TODO
Test-Tester-0.103/ARTISTIC
Test-Tester-0.103/MANIFEST
Removing previously used /root/.cpan/build/Test-Tester-0.103

  CPAN.pm: Going to build F/FD/FDALY/Test-Tester-0.103.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for Test::Tester
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running install for module Test::NoWarnings
Running make for F/FD/FDALY/Test-NoWarnings-0.082.tar.gz
Checksum for /root/.cpan/sources/authors/id/F/FD/FDALY/Test-NoWarnings-0.082.tar.gz ok
Test-NoWarnings-0.082/
Test-NoWarnings-0.082/Makefile.PL
Test-NoWarnings-0.082/LGPL
Test-NoWarnings-0.082/META.yml
Test-NoWarnings-0.082/t/
Test-NoWarnings-0.082/t/none.t
Test-NoWarnings-0.082/t/no_tests.t
Test-NoWarnings-0.082/t/end.t
Test-NoWarnings-0.082/t/no_end.t
Test-NoWarnings-0.082/t/fork.t
Test-NoWarnings-0.082/CHANGES
Test-NoWarnings-0.082/README
Test-NoWarnings-0.082/lib/
Test-NoWarnings-0.082/lib/Test/
Test-NoWarnings-0.082/lib/Test/NoWarnings.pm
Test-NoWarnings-0.082/lib/Test/NoWarnings/
Test-NoWarnings-0.082/lib/Test/NoWarnings/Warning.pm
Test-NoWarnings-0.082/MANIFEST
Removing previously used /root/.cpan/build/Test-NoWarnings-0.082

  CPAN.pm: Going to build F/FD/FDALY/Test-NoWarnings-0.082.tar.gz

Checking if your kit is complete...
Looks good
Warning: prerequisite Test::Tester 0.103 not found.
Writing Makefile for Test::NoWarnings
---- Unsatisfied dependencies detected during [F/FD/FDALY/Test-NoWarnings-0.082.tar.gz] -----
    Test::Tester
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes]
Running make test
  Delayed until after prerequisites
Running make install
  Delayed until after prerequisites
Running install for module Test::Tester
Running make for F/FD/FDALY/Test-Tester-0.103.tar.gz
Checksum for /root/.cpan/sources/authors/id/F/FD/FDALY/Test-Tester-0.103.tar.gz ok
Test-Tester-0.103/
Test-Tester-0.103/Makefile.PL
Test-Tester-0.103/META.yml
Test-Tester-0.103/t/
Test-Tester-0.103/t/fail/
Test-Tester-0.103/t/fail/fail.t
Test-Tester-0.103/t/MyTest.pm
Test-Tester-0.103/t/run_test.t
Test-Tester-0.103/t/capture.t
Test-Tester-0.103/t/auto.t
Test-Tester-0.103/t/check_tests.t
Test-Tester-0.103/t/SmallTest.pm
Test-Tester-0.103/t/depth.t
Test-Tester-0.103/CHANGES
Test-Tester-0.103/README
Test-Tester-0.103/lib/
Test-Tester-0.103/lib/Test/
Test-Tester-0.103/lib/Test/Tester/
Test-Tester-0.103/lib/Test/Tester/CaptureRunner.pm
Test-Tester-0.103/lib/Test/Tester/Delegate.pm
Test-Tester-0.103/lib/Test/Tester/Capture.pm
Test-Tester-0.103/lib/Test/Tester.pm
Test-Tester-0.103/TODO
Test-Tester-0.103/ARTISTIC
Test-Tester-0.103/MANIFEST
Removing previously used /root/.cpan/build/Test-Tester-0.103

  CPAN.pm: Going to build F/FD/FDALY/Test-Tester-0.103.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for Test::Tester
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running install for module Test::NoWarnings
Running make for F/FD/FDALY/Test-NoWarnings-0.082.tar.gz
Checksum for /root/.cpan/sources/authors/id/F/FD/FDALY/Test-NoWarnings-0.082.tar.gz ok
Test-NoWarnings-0.082/
Test-NoWarnings-0.082/Makefile.PL
Test-NoWarnings-0.082/LGPL
Test-NoWarnings-0.082/META.yml
Test-NoWarnings-0.082/t/
Test-NoWarnings-0.082/t/none.t
Test-NoWarnings-0.082/t/no_tests.t
Test-NoWarnings-0.082/t/end.t
Test-NoWarnings-0.082/t/no_end.t
Test-NoWarnings-0.082/t/fork.t
Test-NoWarnings-0.082/CHANGES
Test-NoWarnings-0.082/README
Test-NoWarnings-0.082/lib/
Test-NoWarnings-0.082/lib/Test/
Test-NoWarnings-0.082/lib/Test/NoWarnings.pm
Test-NoWarnings-0.082/lib/Test/NoWarnings/
Test-NoWarnings-0.082/lib/Test/NoWarnings/Warning.pm
Test-NoWarnings-0.082/MANIFEST
Removing previously used /root/.cpan/build/Test-NoWarnings-0.082

  CPAN.pm: Going to build F/FD/FDALY/Test-NoWarnings-0.082.tar.gz

Checking if your kit is complete...
Looks good
Warning: prerequisite Test::Tester 0.103 not found.
Writing Makefile for Test::NoWarnings
---- Unsatisfied dependencies detected during [F/FD/FDALY/Test-NoWarnings-0.082.tar.gz] -----
    Test::Tester
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes]

Running make test
  Delayed until after prerequisites
Running make install
  Delayed until after prerequisites
Running install for module Test::Tester
Running make for F/FD/FDALY/Test-Tester-0.103.tar.gz
  Is already unwrapped into directory /root/.cpan/build/Test-Tester-0.103
  Has already been processed within this session
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running make for F/FD/FDALY/Test-NoWarnings-0.082.tar.gz
  Is already unwrapped into directory /root/.cpan/build/Test-NoWarnings-0.082

  CPAN.pm: Going to build F/FD/FDALY/Test-NoWarnings-0.082.tar.gz

    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running make for F/FD/FDALY/Test-Deep-0.095.tar.gz
  Is already unwrapped into directory /root/.cpan/build/Test-Deep-0.095

  CPAN.pm: Going to build F/FD/FDALY/Test-Deep-0.095.tar.gz

    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running make for C/CW/CWEST/Apache-Session-1.81.tar.gz
  Is already unwrapped into directory /root/.cpan/build/Apache-Session-1.81

  CPAN.pm: Going to build C/CW/CWEST/Apache-Session-1.81.tar.gz

    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
root@it002:~#
```

Thanks,

Ozz.

---

### Post by Hezekiah on 2006-08-14
You may want to try:
```

install Bundle::CPAN

```
from within the CPAN shell.  Quit cpan first though (quit is the command to do so), as it caches certain things during a run which may need manual flushing here and there.  If that process doesn't work, then there may be some other issue - either missing package, or who knows what else.

I'm not sure why you are getting those "Writing Makefile for Some::Package -- NOT OK" - I don't remember seeing those errors before.

I'll try to look around a bit more, but like I said I'm not sure why you're getting the errors that you are.

---

### Post by Hezekiah on 2006-08-14
Ah ha!  I think I found it :-)

The problem is (apparently) that the cpan shell was configured on your computer before make was available - or for some other reason the make executable wasn't found.

In order to fix this, you will need to reconfigure cpan.

Start up the cpan shell as before:
```

sudo su - root
cpan

```

Then, in the cpan shell, type the command:
```

o conf init

```
and follow the prompts.  The biggest pain while setting this up is, in my opinion, picking a good mirror.  But if you pick a few near your physical location (or ping them manually from another terminal to test them) you should be in decent shape.

Once all of that configuration is complete, try installing the packages again.  With luck, it will work - and if not, you should at least get new errors!

Good luck!

---

### Post by Ozz on 2006-08-14
Still geting the same errors.... :confused: 
frustrating....

I might have to try a different server, debian or Gentoo...
Oh well...

Will take a look at cpan and see if they have anything new. 

EDIT: had not seen your last post. I will try and get back to you.

Ozz.

---

### Post by Ozz on 2006-08-14
Looks like there's some movement forward... 
Thank you so much for all the support and I'll try to gather new errors and post back.

Ozz.

---

### Post by Ozz on 2006-08-14
Hi there Hezekiah, here's probably the final stop before I'm through:
```
root@it002:~# cpan install Apache::Session
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Sun, 13 Aug 2006 19:29:57 GMT
Running install for module install
Running make for J/JU/JUNOS/junoscript-perl-6.4I0.tar.gz
CPAN: Digest::MD5 loaded ok
CPAN: Compress::Zlib loaded ok
Checksum for /root/.cpan/sources/authors/id/J/JU/JUNOS/junoscript-perl-6.4I0.tar                                                                             .gz ok
Scanning cache /root/.cpan/build for sizes
Deleting from cache: /root/.cpan/build/Bundle-libnet-1.00 (11.0>10.0 MB)
Deleting from cache: /root/.cpan/build/Bundle-CPAN-1.852 (11.0>10.0 MB)
Deleting from cache: /root/.cpan/build/Apache-Test-1.28 (11.0>10.0 MB)
Deleting from cache: /root/.cpan/build/Digest-SHA-5.43 (10.5>10.0 MB)
Deleting from cache: /root/.cpan/build/File-HomeDir-0.58 (10.2>10.0 MB)
Deleting from cache: /root/.cpan/build/PathTools-3.19 (10.1>10.0 MB)
junoscript-perl-6.4I0/
junoscript-perl-6.4I0/lib/
junoscript-perl-6.4I0/lib/JUNOS/
junoscript-perl-6.4I0/lib/JUNOS/Access/
junoscript-perl-6.4I0/lib/JUNOS/Access/stubs.pm
junoscript-perl-6.4I0/lib/JUNOS/Access/clear_text.pm
junoscript-perl-6.4I0/lib/JUNOS/Access/ssh.pm
junoscript-perl-6.4I0/lib/JUNOS/Access/ssl.pm
junoscript-perl-6.4I0/lib/JUNOS/Access/xnm.pm
junoscript-perl-6.4I0/lib/JUNOS/Access/telnet.pm
junoscript-perl-6.4I0/lib/JUNOS/Access/rsh.pm
junoscript-perl-6.4I0/lib/JUNOS/Access.pm
junoscript-perl-6.4I0/lib/JUNOS/Methods.pm
junoscript-perl-6.4I0/lib/JUNOS/DOM/
junoscript-perl-6.4I0/lib/JUNOS/DOM/Parser.pm
junoscript-perl-6.4I0/lib/JUNOS/6.4I0/
junoscript-perl-6.4I0/lib/JUNOS/6.4I0/jkernel_methods.pl
junoscript-perl-6.4I0/lib/JUNOS/6.4I0/jroute_methods.pl
junoscript-perl-6.4I0/lib/JUNOS/6.4I0/jcrypto_methods.pl
junoscript-perl-6.4I0/lib/JUNOS/Response.pm
junoscript-perl-6.4I0/lib/JUNOS/version.pm
junoscript-perl-6.4I0/lib/JUNOS/Trace.pm
junoscript-perl-6.4I0/lib/JUNOS/Device.pm
junoscript-perl-6.4I0/examples/
junoscript-perl-6.4I0/examples/get_chassis_inventory/
junoscript-perl-6.4I0/examples/get_chassis_inventory/banner_logo.gif
junoscript-perl-6.4I0/examples/get_chassis_inventory/xsl/
junoscript-perl-6.4I0/examples/get_chassis_inventory/xsl/chassis_inventory_csv.x                                                                             sl
junoscript-perl-6.4I0/examples/get_chassis_inventory/xsl/chassis_inventory_xml.x                                                                             sl
junoscript-perl-6.4I0/examples/get_chassis_inventory/xsl/chassis_inventory_html.                                                                             xsl
junoscript-perl-6.4I0/examples/get_chassis_inventory/get_chassis_inventory.pl
junoscript-perl-6.4I0/examples/RDB/
junoscript-perl-6.4I0/examples/RDB/README
junoscript-perl-6.4I0/examples/RDB/common.pm
junoscript-perl-6.4I0/examples/RDB/unpop_tables.pl
junoscript-perl-6.4I0/examples/RDB/get_config.pl
junoscript-perl-6.4I0/examples/RDB/pop_tables.pl
junoscript-perl-6.4I0/examples/RDB/make_tables.pl
junoscript-perl-6.4I0/examples/load_configuration/
junoscript-perl-6.4I0/examples/load_configuration/requests/
junoscript-perl-6.4I0/examples/load_configuration/requests/set_login_user_foo.xm                                                                             l
junoscript-perl-6.4I0/examples/load_configuration/requests/set_login_class_bar.x                                                                             ml
junoscript-perl-6.4I0/examples/load_configuration/load_configuration.pl
junoscript-perl-6.4I0/examples/diagnose_bgp/
junoscript-perl-6.4I0/examples/diagnose_bgp/js/
junoscript-perl-6.4I0/examples/diagnose_bgp/js/sorttable.js
junoscript-perl-6.4I0/examples/diagnose_bgp/xsl/
junoscript-perl-6.4I0/examples/diagnose_bgp/xsl/text.xsl
junoscript-perl-6.4I0/examples/diagnose_bgp/xsl/html.xsl
junoscript-perl-6.4I0/examples/diagnose_bgp/xsl/dhtml.xsl
junoscript-perl-6.4I0/examples/diagnose_bgp/diagnose_bgp.pl
junoscript-perl-6.4I0/banner_logo.gif
junoscript-perl-6.4I0/MANIFEST
junoscript-perl-6.4I0/CHANGES
junoscript-perl-6.4I0/to_topg.gif
junoscript-perl-6.4I0/install.pm
junoscript-perl-6.4I0/Makefile.PL
junoscript-perl-6.4I0/README
junoscript-perl-6.4I0/install-prereqs.pl
junoscript-perl-6.4I0/README.html
junoscript-perl-6.4I0/required-mod.pl
junoscript-perl-6.4I0/access/
junoscript-perl-6.4I0/access/ssh.pm
junoscript-perl-6.4I0/access/ssl.pm
junoscript-perl-6.4I0/t/
junoscript-perl-6.4I0/t/base-1.t
junoscript-perl-6.4I0/t/base-2.t
Removing previously used /root/.cpan/build/junoscript-perl-6.4I0

  CPAN.pm: Going to build J/JU/JUNOS/junoscript-perl-6.4I0.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for junoscript-perl
cp lib/JUNOS/Access/clear_text.pm blib/lib/JUNOS/Access/clear_text.pm
cp lib/JUNOS/Access/stubs.pm blib/lib/JUNOS/Access/stubs.pm
cp lib/JUNOS/Methods.pm blib/lib/JUNOS/Methods.pm
cp lib/JUNOS/Access.pm blib/lib/JUNOS/Access.pm
cp lib/JUNOS/Response.pm blib/lib/JUNOS/Response.pm
cp lib/JUNOS/Access/ssh.pm blib/lib/JUNOS/Access/ssh.pm
cp lib/JUNOS/Device.pm blib/lib/JUNOS/Device.pm
cp lib/JUNOS/6.4I0/jkernel_methods.pl blib/lib/JUNOS/6.4I0/jkernel_methods.pl
cp lib/JUNOS/version.pm blib/lib/JUNOS/version.pm
cp lib/JUNOS/6.4I0/jcrypto_methods.pl blib/lib/JUNOS/6.4I0/jcrypto_methods.pl
cp lib/JUNOS/Trace.pm blib/lib/JUNOS/Trace.pm
cp lib/JUNOS/Access/xnm.pm blib/lib/JUNOS/Access/xnm.pm
cp lib/JUNOS/6.4I0/jroute_methods.pl blib/lib/JUNOS/6.4I0/jroute_methods.pl
cp lib/JUNOS/Access/ssl.pm blib/lib/JUNOS/Access/ssl.pm
cp lib/JUNOS/Access/rsh.pm blib/lib/JUNOS/Access/rsh.pm
cp lib/JUNOS/Access/telnet.pm blib/lib/JUNOS/Access/telnet.pm
cp lib/JUNOS/DOM/Parser.pm blib/lib/JUNOS/DOM/Parser.pm
Manifying blib/man3/JUNOS::Access::clear_text.3pm
Manifying blib/man3/JUNOS::Access::stubs.3pm
Manifying blib/man3/JUNOS::Methods.3pm
Manifying blib/man3/JUNOS::Access.3pm
Manifying blib/man3/JUNOS::Access::ssh.3pm
Manifying blib/man3/JUNOS::Response.3pm
Manifying blib/man3/JUNOS::Access::ssl.3pm
Manifying blib/man3/JUNOS::Access::rsh.3pm
Manifying blib/man3/JUNOS::Device.3pm
Manifying blib/man3/JUNOS::Access::telnet.3pm
Manifying blib/man3/JUNOS::Access::xnm.3pm
Manifying blib/man3/JUNOS::Trace.3pm
Manifying blib/man3/JUNOS::DOM::Parser.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0,                                                                              'blib/lib', 'blib/arch')" t/*.t
t/base-1....ok 1/5Use of uninitialized value in numeric eq (==) at /usr/local/sh                                                                             are/perl/5.8.7/XML/DOM.pm line 4435.
Use of uninitialized value in numeric eq (==) at /usr/local/share/perl/5.8.7/XML                                                                             /DOM.pm line 4435.
Use of uninitialized value in numeric eq (==) at /usr/local/share/perl/5.8.7/XML                                                                             /DOM.pm line 4435.
t/base-1....ok
t/base-2....ok 1/7Use of uninitialized value in numeric eq (==) at /usr/local/sh                                                                             are/perl/5.8.7/XML/DOM.pm line 4435.
Use of uninitialized value in concatenation (.) or string at /root/.cpan/build/j                                                                             unoscript-perl-6.4I0/blib/lib/JUNOS/Response.pm line 93.
Use of uninitialized value in numeric eq (==) at /usr/local/share/perl/5.8.7/XML                                                                             /DOM.pm line 4435.
t/base-2....ok
All tests successful.
Files=2, Tests=12,  1 wallclock secs ( 0.41 cusr +  0.01 csys =  0.42 CPU)
  /usr/bin/make test -- OK
Running make install
Writing /usr/local/lib/perl/5.8.7/auto/junoscript-perl/.packlist
Appending installation info to /usr/local/lib/perl/5.8.7/perllocal.pod
make: *** No rule to make target `1'.  Stop.
  /usr/bin/make install 1 -- NOT OK
Apache::Session is up to date.
root@it002:~#

```

Ozz.

---

### Post by Ozz on 2006-08-14
Hezekiah, I cannot thank you enough!
I'm through to the next step.

All gui based from now on, I will not forget this install though :mrgreen: 

Ozz.

---

### Post by vando on 2006-08-23
Hi All,

I am new to this forum. Was just googling around and found out that someone has the same error as me. Well, just this error below after successfully installing a package via cpan.

Appending installation info to /usr/local/lib/perl/5.8.7/perllocal.pod
make: *** No rule to make target `1'.  Stop.
  /usr/bin/make install 1 -- NOT OK

Basically, everytime I install a perl package via cpan I get the above error.  However, everything installed fine, it just that I get this last message.  Thanks all!!

---

### Post by Ozz on 2006-08-24
I had this error and ignored it and the install went well so I'm not saying this will be the case there as I'm not well versed in CPAN matters, but I would go ahead and see how the system behaves.

Ozz.

---

