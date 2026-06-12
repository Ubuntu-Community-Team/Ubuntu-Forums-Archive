---
title: "Problem Oracle client + Ubuntu 10.4"
date: 2011-01-24
forum: Server Platforms
---

### Post by salvades on 2011-01-24
I installed the oracle on ubuntu-server clientt 10.4, now I need to incorporate a Nagios plugin to monitor oracle databases, the steps I performed are:

Rpm packages to parse the alien utility

oracle-instantclient-basiclite-10.2.0.3-1.i386.rpm
oracle-instantclient-devel-10.2.0.3-1.i386.rpm
oracle-instantclient-sqlplus-10.2.0.3-1.i386.rpm

I connect using sqlplus

root@Ubuntu01-nagios# sqlplus monitor/lala2010@//172.16.44.101:1521/mprod_01 
SQL*Plus: Release 10.2.0.3.0 - Production on Mon Jan 24 15:15:57 2011 
Copyright (c) 1982, 2006, Oracle.  All Rights Reserved. 

Later while trying to use the nagios plugins that I claimed for the driver DBD:: Oracle

root@Ubuntu01-nagios:/usr/lib/nagios/plugins# ./check_oracle_health --connect 172.16.44.101 --user monitor --password lala2010 --mode tablespace-usage 
CRITICAL - cannot connect to 172.20.10.180. install_driver(Oracle) failed: Can't locate DBD/Oracle.pm in @INC (@INC contains: . /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl) at (eval 18) line 3. 
Perhaps the DBD::Oracle perl module hasn't been fully installed, 
or perhaps the capitalisation of 'Oracle' isn't right. 
Available drivers: AnyData, CSV, DBM, ExampleP, File, Gofer, LDAP, ODBC, Proxy, Sponge, Sybase, mysql. 
 at ./check_oracle_health line 4596 

**This is where my problem starts, I found this way to install the module DBD:: Oracle, the steps I followed:**


root@Ubuntu01-nagios:/usr/lib/nagios/plugins# perl -MCPAN -e shell 
Terminal does not support AddHistory. 
cpan shell -- CPAN exploration and modules installation (v1.9402) 
Enter 'h' for help. 

cpan[1]> install DBD::Oracle 
CPAN: Storable loaded ok (v2.20) 
Going to read '/root/.cpan/Metadata' 
  Database was generated on Mon, 24 Jan 2011 13:35:26 GMT 
Running install for module 'DBD::Oracle' 
CPAN: YAML loaded ok (v0.71) 
Running make for P/PY/PYTHIAN/DBD-Oracle-1.27.tar.gz 
CPAN: Digest::SHA loaded ok (v5.47) 
CPAN: Compress::Zlib loaded ok (v2.02) 
Checksum for /root/.cpan/sources/authors/id/P/PY/PYTHIAN/DBD-Oracle-1.27.tar.gz ok 
Scanning cache /root/.cpan/build for sizes 
............................................................................DONE 
CPAN: Archive::Tar loaded ok (v1.52) 
DBD-Oracle-1.27/ 
DBD-Oracle-1.27/README.java.txt 
DBD-Oracle-1.27/t/ 
DBD-Oracle-1.27/t/55nested.t 
DBD-Oracle-1.27/t/23wide_db.t 
DBD-Oracle-1.27/t/10general.t 
DBD-Oracle-1.27/t/80ora_charset.t 
DBD-Oracle-1.27/t/31lob_extended.t 
DBD-Oracle-1.27/t/58object.t 
DBD-Oracle-1.27/t/26exe_array.t 
DBD-Oracle-1.27/t/22nchar_utf8.t 
DBD-Oracle-1.27/t/40ph_type.t 
DBD-Oracle-1.27/t/21nchar.t 
DBD-Oracle-1.27/t/22nchar_al32utf8.t 
DBD-Oracle-1.27/t/14threads.t 
DBD-Oracle-1.27/t/56embbeded.t 
DBD-Oracle-1.27/t/51scroll.t 
DBD-Oracle-1.27/t/15nls.t 
DBD-Oracle-1.27/t/60reauth.t 
DBD-Oracle-1.27/t/25plsql.t 
DBD-Oracle-1.27/t/34pres_lobs.t 
DBD-Oracle-1.27/t/23wide_db_8bit.t 
DBD-Oracle-1.27/t/28array_bind.t 
DBD-Oracle-1.27/t/24implicit_utf8.t 
DBD-Oracle-1.27/t/nchar_test_lib.pl 
DBD-Oracle-1.27/t/50cursor.t 
DBD-Oracle-1.27/t/32xmltype.t 
DBD-Oracle-1.27/t/23wide_db_al32utf8.t 
DBD-Oracle-1.27/t/20select.t 
DBD-Oracle-1.27/t/12impdata.t 
DBD-Oracle-1.27/t/70meta.t 
DBD-Oracle-1.27/t/31lob.t 
DBD-Oracle-1.27/t/30long.t 
DBD-Oracle-1.27/t/01base.t 
DBD-Oracle-1.27/Oracle.ex/ 
DBD-Oracle-1.27/Oracle.ex/README 
DBD-Oracle-1.27/Oracle.ex/sql 
DBD-Oracle-1.27/Oracle.ex/bind.pl 
DBD-Oracle-1.27/Oracle.ex/commit.pl 
DBD-Oracle-1.27/Oracle.ex/tabinfo.pl 
DBD-Oracle-1.27/Oracle.ex/ex.pl 
DBD-Oracle-1.27/Oracle.ex/curref.pl 
DBD-Oracle-1.27/Oracle.ex/japh 
DBD-Oracle-1.27/Oracle.ex/proc.pl 
DBD-Oracle-1.27/Oracle.ex/mktable.pl 
DBD-Oracle-1.27/Oracle.ex/oradump.pl 
DBD-Oracle-1.27/Changes 
DBD-Oracle-1.27/Oracle.h 
DBD-Oracle-1.27/MANIFEST 
DBD-Oracle-1.27/typemap 
DBD-Oracle-1.27/README-files/ 
DBD-Oracle-1.27/README-files/hpux/ 
DBD-Oracle-1.27/README-files/hpux/Conf-Merijn-588-11.11-gcc64 
DBD-Oracle-1.27/README-files/hpux/Conf-Mike 
DBD-Oracle-1.27/README-files/hpux/Conf-Merijn-588-10.20-gcc 
DBD-Oracle-1.27/README-files/hpux/Conf-Lincoln-1.06 
DBD-Oracle-1.27/README-files/hpux/Conf-Merijn-588-11.11-gcc32 
DBD-Oracle-1.27/README-files/hpux/Makefile-Lincoln 
DBD-Oracle-1.27/README-files/hpux/Conf-Merijn-585-11.00-cc 
DBD-Oracle-1.27/README-files/hpux/Conf-Roger 
DBD-Oracle-1.27/README-files/hpux/Conf-Merijn-588-11.00-gcc64 
DBD-Oracle-1.27/README-files/hpux/Conf-Lincoln-1.07 
DBD-Oracle-1.27/README-files/hpux/libjava.eml 
DBD-Oracle-1.27/README-files/hpux/Conf-Merijn-580-10.20-cc 
DBD-Oracle-1.27/README-files/hpux/Conf-Merijn-588-11.00-gcc32 
DBD-Oracle-1.27/README-files/hpux/Conf-Merijn-587-11.23-cc 
DBD-Oracle-1.27/README-files/hpux/Conf-Merijn-585-11.11-cc 
DBD-Oracle-1.27/README-files/hpux/Conf-Merijn-588-11.23-gcc64 
DBD-Oracle-1.27/README.hpux.txt 
DBD-Oracle-1.27/lib/ 
DBD-Oracle-1.27/lib/DBD/ 
DBD-Oracle-1.27/lib/DBD/Oracle/ 
DBD-Oracle-1.27/lib/DBD/Oracle/GetInfo.pm 
DBD-Oracle-1.27/lib/DBD/Oracle/Object.pm 
DBD-Oracle-1.27/dbdimp.c 
DBD-Oracle-1.27/README.login.txt 
DBD-Oracle-1.27/README.linux.txt 
DBD-Oracle-1.27/README.vms.txt 
DBD-Oracle-1.27/README.win32.txt 
DBD-Oracle-1.27/hints/ 
DBD-Oracle-1.27/hints/macos_syms.pl 
DBD-Oracle-1.27/hints/svr4.pl 
DBD-Oracle-1.27/hints/macos_bundle.syms 
DBD-Oracle-1.27/hints/dgux.pl 
DBD-Oracle-1.27/hints/macos_lib.syms 
DBD-Oracle-1.27/oraperl.ph 
DBD-Oracle-1.27/README.longs.txt 
DBD-Oracle-1.27/README.macosx.txt 
DBD-Oracle-1.27/README.win64.txt 
DBD-Oracle-1.27/test.pl 
DBD-Oracle-1.27/oci.def 
DBD-Oracle-1.27/Todo 
DBD-Oracle-1.27/Oraperl.pm 
DBD-Oracle-1.27/README.help.txt 
DBD-Oracle-1.27/README.explain.txt 
DBD-Oracle-1.27/README 
DBD-Oracle-1.27/ora_explain.PL 
DBD-Oracle-1.27/README.sec.txt 
DBD-Oracle-1.27/oci8.c 
DBD-Oracle-1.27/README.wingcc.txt 
DBD-Oracle-1.27/dbdimp.h 
DBD-Oracle-1.27/ocitrace.h 
DBD-Oracle-1.27/Oracle.xs 
DBD-Oracle-1.27/README.sun.txt 
DBD-Oracle-1.27/Oracle.pm 
DBD-Oracle-1.27/dbivport.h 
DBD-Oracle-1.27/README.clients.txt 
DBD-Oracle-1.27/mkta.pl 
DBD-Oracle-1.27/README.aix.txt 
DBD-Oracle-1.27/Makefile.PL 
DBD-Oracle-1.27/README.64bit.txt 
DBD-Oracle-1.27/META.yml 
CPAN: File::Temp loaded ok (v0.22) 
CPAN.pm: Going to build P/PY/PYTHIAN/DBD-Oracle-1.27.tar.gz 
Multiple copies of Driver.xst found in: /usr/local/lib/perl/5.10.1/auto/DBI/ /usr/lib/perl5/auto/DBI/ at Makefile.PL line 37 
Using DBI 1.616 (for perl 5.010001 on i486-linux-gnu-thread-multi) installed in /usr/local/lib/perl/5.10.1/auto/DBI/ 
Argument "6.55_02" isn't numeric in numeric ge (>=) at Makefile.PL line 64. 
Configuring DBD::Oracle for perl 5.010001 on linux (i486-linux-gnu-thread-multi) 
Remember to actually *READ* the README file! Especially if you have any problems. 



Trying to find an ORACLE_HOME 
Your LD_LIBRARY_PATH env var is set to '' 

      The ORACLE_HOME environment variable is not set and I couldn't guess it. 
      It must be set to hold the path to an Oracle installation directory 
      on this machine (or a machine with a compatible architecture). 
      See the appropriate README file for your OS for more information. 
      ABORTED! 
  
Warning: No success on command[/usr/bin/perl Makefile.PL INSTALLDIRS=site] 
  PYTHIAN/DBD-Oracle-1.27.tar.gz 
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK 
Running make test 
  Make had some problems, won't test 
Running make install 
  Make had some problems, won't install 
Failed during this command: 
 PYTHIAN/DBD-Oracle-1.27.tar.gz               : writemakefile NO '/usr/bin/perl Makefile.PL INSTALLDIRS=site' returned status 65280 

I was researching that ubuntu needs Oracle environment variables, so that procedure fix it, according to the attached documentation, write to initialize variables in the file

root@Ubuntu01-nagios:/usr/lib/nagios/plugins# cat /etc/ld.so.conf.d/oracle.conf 

/usr/lib/oracle/10.2.0.3/client/lib 

Fuentes Blog: 
[http://zidboy.blogspot.com/2008/05/intalar-cliente-oracle-10g-y-tora-en.html](http://zidboy.blogspot.com/2008/05/intalar-cliente-oracle-10g-y-tora-en.html)
[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

Moreover also I have initialized the environment variables in the file:

cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games" 
# Configuracion de ORACLE 
ORACLE_HOME=/usr/lib/oracle/10.2.0.3 
LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH 
export LD_LIBRARY_PATH=/usr/lib/oracle/10.2.0.3/client/lib 
export ORACLE_HOME=/usr/lib/oracle/10.2.0.3/client 
#export TNS_ADMIN=<directorio tnsnames.ora> 

I tried commenting the environment variables and only use the declared in /etc/ld.so.conf.d/oracle.conf and vice versa, but always with the same result.



Trying to find an ORACLE_HOME 
Your LD_LIBRARY_PATH env var is set to '' 


any help colleagues Ubunteros
Greetings from Chile
salvades

---

### Post by Vegan on 2011-01-24
You might want to go inquire on the Oracle forums, they are better equipped to help.

Ubuntu uses MySQL as the default.

---

