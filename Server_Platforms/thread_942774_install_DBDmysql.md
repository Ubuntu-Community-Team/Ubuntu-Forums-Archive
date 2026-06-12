---
title: "install DBD::mysql"
date: 2008-10-09
forum: Server Platforms
---

### Post by Sil2 on 2008-10-09
Hi world!

I really need DBD::mysql installed but I'm receiving  "Can't exec mysql_config" errors during installation process. 
I tried search web about any solution and did many things and steps but still no success. 
Please advise!  

I have ubuntu server latest version. 
perl, mysql, cpan etc... everything installed and updated.

**This is my installation log bellow:**
[I]cpan>   install DBD::mysql
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Wed, 08 Oct 2008 19:28:23 GMT
Running install for module DBD::mysql
Running make for C/CA/CAPTTOFU/DBD-mysql-4.008.tar.gz
CPAN: Digest::MD5 loaded ok
Checksum for /root/.cpan/sources/authors/id/C/CA/CAPTTOFU/DBD-mysql-4.008.tar.gz ok
Scanning cache /root/.cpan/build for sizes
DBD-mysql-4.008/
DBD-mysql-4.008/ChangeLog
DBD-mysql-4.008/constants.h
DBD-mysql-4.008/dbdimp.c
DBD-mysql-4.008/dbdimp.h
DBD-mysql-4.008/eg/
DBD-mysql-4.008/eg/._bug14979.pl
DBD-mysql-4.008/eg/bug14979.pl
DBD-mysql-4.008/eg/._bug21028.pl
DBD-mysql-4.008/eg/bug21028.pl
DBD-mysql-4.008/eg/bug30033.pl
DBD-mysql-4.008/eg/bug30033pg.pl
DBD-mysql-4.008/eg/decimal_test.pl
DBD-mysql-4.008/eg/issue21946.pl
DBD-mysql-4.008/eg/prepare_memory_usage.pl
DBD-mysql-4.008/eg/proc_example1.pl
DBD-mysql-4.008/eg/proc_example2.pl
DBD-mysql-4.008/eg/proc_example2a.pl
DBD-mysql-4.008/eg/proc_example2b.pl
DBD-mysql-4.008/eg/proc_example3.pl
DBD-mysql-4.008/eg/proc_example4.pl
DBD-mysql-4.008/INSTALL.html
DBD-mysql-4.008/lib/
DBD-mysql-4.008/lib/Bundle/
DBD-mysql-4.008/lib/Bundle/DBD/
DBD-mysql-4.008/lib/Bundle/DBD/mysql.pm
DBD-mysql-4.008/lib/DBD/
DBD-mysql-4.008/lib/DBD/mysql/
DBD-mysql-4.008/lib/DBD/mysql/GetInfo.pm
DBD-mysql-4.008/lib/DBD/mysql/INSTALL.pod
DBD-mysql-4.008/lib/DBD/mysql.pm
DBD-mysql-4.008/Makefile.PL
DBD-mysql-4.008/Makefile.PL.embedded
DBD-mysql-4.008/MANIFEST
DBD-mysql-4.008/MANIFEST.SKIP
DBD-mysql-4.008/META.yml
DBD-mysql-4.008/myld
DBD-mysql-4.008/mysql.xs
DBD-mysql-4.008/README
DBD-mysql-4.008/t/
DBD-mysql-4.008/t/00base.t
DBD-mysql-4.008/t/10connect.t
DBD-mysql-4.008/t/20createdrop.t
DBD-mysql-4.008/t/25lockunlock.t
DBD-mysql-4.008/t/29warnings.t
DBD-mysql-4.008/t/30insertfetch.t
DBD-mysql-4.008/t/31insertid.t
DBD-mysql-4.008/t/32insert_error.t
DBD-mysql-4.008/t/35limit.t
DBD-mysql-4.008/t/35prepare.t
DBD-mysql-4.008/t/40bindparam.t
DBD-mysql-4.008/t/40bindparam2.t
DBD-mysql-4.008/t/40blobs.t
DBD-mysql-4.008/t/40catalog.t
DBD-mysql-4.008/t/40keyinfo.t
DBD-mysql-4.008/t/40listfields.t
DBD-mysql-4.008/t/40nulls.t
DBD-mysql-4.008/t/40numrows.t
DBD-mysql-4.008/t/40server_prepare.t
DBD-mysql-4.008/t/40server_prepare_error.t
DBD-mysql-4.008/t/40types.t
DBD-mysql-4.008/t/41bindparam.t
DBD-mysql-4.008/t/41blobs_prepare.t
DBD-mysql-4.008/t/42bindparam.t
DBD-mysql-4.008/t/50chopblanks.t
DBD-mysql-4.008/t/50commit.t
DBD-mysql-4.008/t/55utf8.t
DBD-mysql-4.008/t/60leaks.t
DBD-mysql-4.008/t/65types.t
DBD-mysql-4.008/t/70takeimp.t
DBD-mysql-4.008/t/._71impdata.t
DBD-mysql-4.008/t/71impdata.t
DBD-mysql-4.008/t/75supported_sql.t
DBD-mysql-4.008/t/76multi_statement.t
DBD-mysql-4.008/t/80procs.t
DBD-mysql-4.008/t/lib.pl
DBD-mysql-4.008/t/mysql.dbtest
DBD-mysql-4.008/t/mysql.mtest
DBD-mysql-4.008/TODO
Removing previously used /root/.cpan/build/DBD-mysql-4.008

  CPAN.pm: Going to build C/CA/CAPTTOFU/DBD-mysql-4.008.tar.gz

Can't exec "mysql_config": No such file or directory at Makefile.PL line 76.

Cannot find the file 'mysql_config'! Your execution PATH doesn't seem
not contain the path to mysql_config. Resorting to guessed values!
Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located


PLEASE NOTE:

For 'make test' to run properly, you must ensure that the
database user 'root' can connect to your MySQL server
and has the proper privileges that these tests require such
as 'drop table', 'create table', 'drop procedure', 'create procedure'
as well as others.

mysql> grant all privileges on test.* to 'root'@'localhost' identified by 's3kr1t';

You can also optionally set the user to run 'make test' with:

perl Makefile.pl --testuser=username

Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Can't exec "mysql_config": No such file or directory at Makefile.PL line 454.
Can't find mysql_config. Use --mysql_config option to specify where mysql_config is located
Failed to determine directory of mysql.h. Use

  perl Makefile.PL --cflags=-I<dir>

to set this directory. For details see the INSTALL.html file,
section "C Compiler flags" or type

  perl Makefile.PL --help
Running make test
  Make had some problems, maybe interrupted? Won't test
Running make install
  Make had some problems, maybe interrupted? Won't install[/I]

---

### Post by Sil2 on 2008-10-14
I found one package to install 
libmysqlclient15-dev
after installation I run again  cpan> install DBD::mysql and got 
different errors

[I]Argument "6.30_01" isn't numeric in numeric ge (>=) at Makefile.PL line 343, <PIPE> line 9             3.
Checking if your kit is complete...
Looks good
Unrecognized argument in LIBS ignored: '-Wl,-Bsymbolic-functions'
Using DBI 1.601 (for perl 5.008008 on i486-linux-gnu-thread-multi) installed in /usr/lib/p             erl5/auto/DBI/
Writing Makefile for DBD::mysql
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible[/I]

---

### Post by Sil2 on 2008-10-14
finally I did few steps more and It looks  like installed but with errors 


**root@ubuntu:~/.cpan/build/DBD-mysql-4.008# perl Makefile.PL --testuser=root --testdb=test**

I will use the following settings for compiling and testing:

  cflags        (mysql_config ) = -I/usr/include/mysql -DBIG_JOINS=1 -fPIC
  embedded      (mysql_config ) =
  libs          (mysql_config ) = -Wl,-Bsymbolic-functions -L/usr/lib/mysql -lmysqlclient
  mysql_config  (guessed      ) = mysql_config
  nocatchstderr (default      ) = 0
  nofoundrows   (default      ) = 0
  ssl           (guessed      ) = 0
  testdb        (User's choice) = test
  testhost      (default      ) =
  testpassword  (default      ) =
  testsocket    (default      ) =
  testuser      (User's choice) = root

To change these settings, see 'perl Makefile.PL --help' and
'perldoc INSTALL'.

Argument "6.30_01" isn't numeric in numeric ge (>=) at Makefile.PL line 343, <PIPE> line 73.
Unrecognized argument in LIBS ignored: '-Wl,-Bsymbolic-functions'
Using DBI 1.601 (for perl 5.008008 on i486-linux-gnu-thread-multi) installed in /usr/lib/perl5/auto/DBI/
Writing Makefile for DBD::mysql
**root@ubuntu:~/.cpan/build/DBD-mysql-4.008# make test**
cc -c  -I/usr/lib/perl5/auto/DBI -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -DDBD_MYSQL_INSERT_ID_IS_GOOD -g  -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"4.008\" -DXS_VERSION=\"4.008\" -fPIC "-I/usr/lib/perl/5.8/CORE"   dbdimp.c
cc -c  -I/usr/lib/perl5/auto/DBI -I/usr/include/mysql -DBIG_JOINS=1 -fPIC -DDBD_MYSQL_INSERT_ID_IS_GOOD -g  -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"4.008\" -DXS_VERSION=\"4.008\" -fPIC "-I/usr/lib/perl/5.8/CORE"   mysql.c
Running Mkbootstrap for DBD::mysql ()
chmod 644 mysql.bs
rm -f blib/arch/auto/DBD/mysql/mysql.so
/usr/bin/perl myld cc  -shared -L/usr/local/lib dbdimp.o mysql.o  -o blib/arch/auto/DBD/mysql/mysql.so  \
           -L/usr/lib/mysql -lmysqlclient       \

chmod 755 blib/arch/auto/DBD/mysql/mysql.so
cp mysql.bs blib/arch/auto/DBD/mysql/mysql.bs
chmod 644 blib/arch/auto/DBD/mysql/mysql.bs
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/00base....................ok
t/10connect.................ok
t/20createdrop..............ok
t/25lockunlock..............ok
t/29warnings................ok
t/30insertfetch.............ok
t/31insertid................ok
t/32insert_error............ok
t/35limit...................ok
t/35prepare.................ok
t/40bindparam...............ok
t/40bindparam2..............ok
t/40blobs...................ok
t/40catalog.................ok
t/40keyinfo.................ok
t/40listfields..............ok
t/40nulls...................ok
t/40numrows.................ok
t/40server_prepare..........ok
t/40server_prepare_error....ok
t/40types...................ok
t/41bindparam...............ok
t/41blobs_prepare...........ok
t/42bindparam...............ok
t/50chopblanks..............ok
t/50commit..................ok
t/55utf8....................ok
t/60leaks...................skipped
        all skipped: Skip $ENV{SLOW_TESTS} is not set
t/65types...................ok
t/70takeimp.................skipped
        all skipped: This test is disabled
t/71impdata.................skipped
        all skipped: This test is disabled
t/75supported_sql...........ok
t/76multi_statement.........ok
t/80procs...................ok
All tests successful, 3 tests skipped.
Files=34, Tests=673, 12 wallclock secs ( 3.74 cusr +  2.39 csys =  6.13 CPU)
**root@ubuntu:~/.cpan/build/DBD-mysql-4.008# make**
Manifying blib/man3/DBD::mysql.3pm
Manifying blib/man3/DBD::mysql::INSTALL.3pm
Manifying blib/man3/Bundle::DBD::mysql.3pm
**root@ubuntu:~/.cpan/build/DBD-mysql-4.008# make install**
Installing /usr/local/lib/perl/5.8.8/auto/DBD/mysql/mysql.so
Installing /usr/local/lib/perl/5.8.8/auto/DBD/mysql/mysql.bs
Files found in blib/arch: installing files in blib/lib into architecture dependent library tree
Installing /usr/local/lib/perl/5.8.8/DBD/mysql.pm
Installing /usr/local/lib/perl/5.8.8/DBD/mysql/INSTALL.pod
Installing /usr/local/lib/perl/5.8.8/DBD/mysql/GetInfo.pm
Installing /usr/local/lib/perl/5.8.8/Bundle/DBD/mysql.pm
Installing /usr/local/man/man3/DBD::mysql::INSTALL.3pm
Installing /usr/local/man/man3/Bundle::DBD::mysql.3pm
Installing /usr/local/man/man3/DBD::mysql.3pm
Writing /usr/local/lib/perl/5.8.8/auto/DBD/mysql/.packlist
Appending installation info to /usr/local/lib/perl/5.8.8/perllocal.pod
**root@ubuntu:~/.cpan/build/DBD-mysql-4.008#**

---

