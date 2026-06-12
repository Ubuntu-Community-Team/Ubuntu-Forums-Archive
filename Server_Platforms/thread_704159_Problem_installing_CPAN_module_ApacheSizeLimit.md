---
title: "Problem installing CPAN module Apache::SizeLimit"
date: 2008-02-22
forum: Server Platforms
---

### Post by Wonka on 2008-02-22
I use Ubuntu Server 7.10 and I'm trying to install the CPAN module Apache::SizeLimit.

Just to make sure I've updated CPAN with:
```

sudo aptitude update
sudo aptitude upgrade
sudo cpan CPAN

```

Then I tried to install Apache::SizeLimit:
```

sudo cpan
cpan[1]>install Apache::SizeLimit

```

All goes well until I receive a big WARNING message:

```

************* WARNING *************

  Your Perl is configured to link against libgdbm,
  but libgdbm.so was not found.
  You could just symlink it to /usr/lib/libgdbm.so.3.0.0


************* WARNING *************
Enter `q' to stop search
Please tell me where I can find your apache src
 [../apache_x.x/src]

```

I already have installed Apache 2, so I don't know why it needs the path for the apache src. I also don't know which path to give. 

If I enter "q" to stop searching I receive the following message:

```

Will run tests as User: 'nobody' Group: 'root'
Checking CGI.pm VERSION..........ok
Checking for LWP::UserAgent......ok
Checking for HTML::HeadParser....ok
Checking if your kit is complete...
Looks good
Writing Makefile for Apache
Writing Makefile for Apache::Connection
Writing Makefile for Apache::Constants
Writing Makefile for Apache::File
Writing Makefile for Apache::Leak
Writing Makefile for Apache::Log
Writing Makefile for Apache::ModuleConfig
Writing Makefile for Apache::PerlRunXS
Writing Makefile for Apache::Server
Writing Makefile for Apache::Symbol
Writing Makefile for Apache::Table
Writing Makefile for Apache::URI
Writing Makefile for Apache::Util
Writing Makefile for mod_perl
cp lib/Apache/Resource.pm blib/lib/Apache/Resource.pm
cp mod_perl_traps.pod blib/lib/mod_perl_traps.pod
cp lib/Apache/src.pm blib/lib/Apache/src.pm
cp lib/Apache/Options.pm blib/lib/Apache/Options.pm
cp mod_perl_method_handlers.pod blib/lib/mod_perl_method_handlers.pod
cp lib/Apache/MyConfig.pm blib/lib/Apache/MyConfig.pm
cp lib/Apache/Opcode.pm blib/lib/Apache/Opcode.pm
cp lib/Apache/httpd_conf.pm blib/lib/Apache/httpd_conf.pm
cp lib/Apache/Debug.pm blib/lib/Apache/Debug.pm
cp cgi_to_mod_perl.pod blib/lib/cgi_to_mod_perl.pod
cp lib/Apache/SizeLimit.pm blib/lib/Apache/SizeLimit.pm
cp lib/Apache/Registry.pm blib/lib/Apache/Registry.pm
cp lib/Apache/PerlRun.pm blib/lib/Apache/PerlRun.pm
cp lib/Apache/FakeRequest.pm blib/lib/Apache/FakeRequest.pm
cp mod_perl_cvs.pod blib/lib/mod_perl_cvs.pod
cp lib/mod_perl.pm blib/lib/mod_perl.pm
cp lib/Apache/fork.pm blib/lib/Apache/fork.pm
cp lib/Apache/RegistryNG.pm blib/lib/Apache/RegistryNG.pm
cp lib/Apache/PerlSections.pm blib/lib/Apache/PerlSections.pm
cp lib/Apache/Include.pm blib/lib/Apache/Include.pm
cp lib/Apache/RegistryBB.pm blib/lib/Apache/RegistryBB.pm
cp lib/mod_perl_hooks.pm.PL blib/lib/mod_perl_hooks.pm.PL
cp lib/Bundle/Apache.pm blib/lib/Bundle/Apache.pm
cp mod_perl_tuning.pod blib/lib/mod_perl_tuning.pod
cp lib/Apache/SIG.pm blib/lib/Apache/SIG.pm
cp mod_perl.pod blib/lib/mod_perl.pod
cp lib/Apache/testold.pm blib/lib/Apache/testold.pm
cp lib/Apache/RedirectLogFix.pm blib/lib/Apache/RedirectLogFix.pm
cp lib/Apache/Constants/Exports.pm blib/lib/Apache/Constants/Exports.pm
cp lib/Apache/StatINC.pm blib/lib/Apache/StatINC.pm
cp lib/mod_perl_hooks.pm blib/lib/mod_perl_hooks.pm
cp lib/Apache/ExtUtils.pm blib/lib/Apache/ExtUtils.pm
cp lib/Apache/Symdump.pm blib/lib/Apache/Symdump.pm
cp lib/Apache/RegistryLoader.pm blib/lib/Apache/RegistryLoader.pm
cp lib/Apache/Status.pm blib/lib/Apache/Status.pm
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Apache'
cp Apache.pm ../blib/lib/Apache.pm
Manifying ../blib/man3/Apache.3pm
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Apache'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Connection'
cp Connection.pm ../blib/lib/Apache/Connection.pm
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Connection'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Constants'
cp Constants.pm ../blib/lib/Apache/Constants.pm
Manifying ../blib/man3/Apache::Constants.3pm
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Constants'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/File'
cp File.pm ../blib/lib/Apache/File.pm
Manifying ../blib/man3/Apache::File.3pm
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/File'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Leak'
cp Leak.pm ../blib/lib/Apache/Leak.pm
/usr/bin/perl /usr/share/perl5/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap -typemap typemap  Leak.xs > Leak.xsc && mv Leak.xsc Leak.c
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"1.00\" -DXS_VERSION=\"1.00\" -fPIC "-I/usr/lib/perl/5.8/CORE"   Leak.c
Running Mkbootstrap for Apache::Leak ()
chmod 644 Leak.bs
rm -f ../blib/arch/auto/Apache/Leak/Leak.so
cc  -shared -L/usr/local/lib Leak.o  -o ../blib/arch/auto/Apache/Leak/Leak.so   \
                \

chmod 755 ../blib/arch/auto/Apache/Leak/Leak.so
cp Leak.bs ../blib/arch/auto/Apache/Leak/Leak.bs
chmod 644 ../blib/arch/auto/Apache/Leak/Leak.bs
Manifying ../blib/man3/Apache::Leak.3pm
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Leak'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Log'
cp Log.pm ../blib/lib/Apache/Log.pm
Manifying ../blib/man3/Apache::Log.3pm
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Log'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/ModuleConfig'
cp ModuleConfig.pm ../blib/lib/Apache/ModuleConfig.pm
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/ModuleConfig'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/PerlRunXS'
cp PerlRunXS.pm ../blib/lib/Apache/PerlRunXS.pm
Manifying ../blib/man3/Apache::PerlRunXS.3pm
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/PerlRunXS'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Server'
cp Server.pm ../blib/lib/Apache/Server.pm
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Server'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Symbol'
cp Symbol.pm ../blib/lib/Apache/Symbol.pm
/usr/bin/perl /usr/share/perl5/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap  Symbol.xs > Symbol.xsc && mv Symbol.xsc Symbol.c
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"1.31\" -DXS_VERSION=\"1.31\" -fPIC "-I/usr/lib/perl/5.8/CORE"   Symbol.c
Running Mkbootstrap for Apache::Symbol ()
chmod 644 Symbol.bs
rm -f ../blib/arch/auto/Apache/Symbol/Symbol.so
cc  -shared -L/usr/local/lib Symbol.o  -o ../blib/arch/auto/Apache/Symbol/Symbol.so     \
                \

chmod 755 ../blib/arch/auto/Apache/Symbol/Symbol.so
cp Symbol.bs ../blib/arch/auto/Apache/Symbol/Symbol.bs
chmod 644 ../blib/arch/auto/Apache/Symbol/Symbol.bs
Manifying ../blib/man3/Apache::Symbol.3pm
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Symbol'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Table'
cp Table.pm ../blib/lib/Apache/Table.pm
Manifying ../blib/man3/Apache::Table.3pm
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Table'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/URI'
cp URI.pm ../blib/lib/Apache/URI.pm
Manifying ../blib/man3/Apache::URI.3pm
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/URI'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Util'
cp Util.pm ../blib/lib/Apache/Util.pm
Manifying ../blib/man3/Apache::Util.3pm
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Util'
Manifying blib/man3/Apache::PerlSections.3pm
Manifying blib/man3/Apache::Resource.3pm
Manifying blib/man3/Apache::Include.3pm
Manifying blib/man3/mod_perl_traps.3pm
Manifying blib/man3/Bundle::Apache.3pm
Manifying blib/man3/mod_perl_tuning.3pm
Manifying blib/man3/Apache::Options.3pm
Manifying blib/man3/Apache::src.3pm
Manifying blib/man3/Apache::SIG.3pm
Manifying blib/man3/mod_perl_method_handlers.3pm
Manifying blib/man3/Apache::MyConfig.3pm
Manifying blib/man3/mod_perl.3pm
Manifying blib/man3/Apache::httpd_conf.3pm
Manifying blib/man3/Apache::Debug.3pm
Manifying blib/man3/cgi_to_mod_perl.3pm
Manifying blib/man3/Apache::testold.3pm
Manifying blib/man3/Apache::RedirectLogFix.3pm
Manifying blib/man3/Apache::StatINC.3pm
Manifying blib/man3/Apache::SizeLimit.3pm
Manifying blib/man3/Apache::Registry.3pm
Manifying blib/man3/Apache::FakeRequest.3pm
Manifying blib/man3/Apache::PerlRun.3pm
Manifying blib/man3/mod_perl_cvs.3pm
Manifying blib/man3/Apache::fork.3pm
Manifying blib/man3/Apache::ExtUtils.3pm
Manifying blib/man3/Apache::Symdump.3pm
Manifying blib/man3/Apache::RegistryLoader.3pm
Manifying blib/man3/Apache::Status.3pm
  GOZER/mod_perl-1.30.tar.gz
  /usr/bin/make -- OK
Running make test
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Apache'
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Apache'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Connection'
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Connection'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Constants'
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Constants'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/File'
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/File'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Leak'
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Leak'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Log'
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Log'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/ModuleConfig'
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/ModuleConfig'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/PerlRunXS'
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/PerlRunXS'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Server'
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Server'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Symbol'
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Symbol'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Table'
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Table'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/URI'
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/URI'
make[1]: Entering directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Util'
make[1]: Leaving directory `/home/mdcuser/.cpan/build/mod_perl-1.30-TJRyHB/Util'
/httpd -f `pwd`/t/conf/httpd.conf -X -d `pwd`/t &
httpd listening on port 8529
will write error_log to: t/logs/error_log
letting apache warm up.../bin/sh: /httpd: not found
done
/usr/bin/perl t/TEST 0
still waiting for server to warm up...............not ok
server failed to start! (please examine t/logs/error_log) at t/TEST line 95.
make: *** [run_tests] Error 111
  GOZER/mod_perl-1.30.tar.gz
  /usr/bin/make test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
  reports GOZER/mod_perl-1.30.tar.gz
Running make install
  make test had returned bad status, won't install without force
Failed during this command:
 GOZER/mod_perl-1.30.tar.gz                   : make_test NO

cpan[2]>

```

Can somebody help me with installing this CPAN package?

---

