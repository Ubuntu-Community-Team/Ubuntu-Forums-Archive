---
title: "Ubuntu-8.04.1-server Install - Cannot install Mysql.pm perl module"
date: 2008-10-23
forum: Server Platforms
---

### Post by rocheteau on 2008-10-23
Hi, 

I have recently installed the 8.04.1 LAMP server but need the Mysql.pm perl module in order for my Perl loading scripts to work. The server is working fine and I have installed Bundle::CPAN. However, at the CPAN prompt the command "install Bundle::DBD::mysql" results in the following error output:
----------------------------------------------------------------------
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
Warning: No success on command[/usr/bin/perl Makefile.PL INSTALLDIRS=site]
  CAPTTOFU/DBD-mysql-4.009.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
Failed during this command:
 CAPTTOFU/DBD-mysql-4.009.tar.gz              : writemakefile NO '/usr/bin/perl Makefile.PL INSTALLDIRS=site' returned status 512
----------------------------------------------------------------------

Any guidance would be greatly appreciated. I have searched online for tips but with very little success. I would have thought that this would be a very prevalent holdup when using the otherwise excellent server installation (I have a server setup with Ubuntu 7 which went without a hitch i.e. no problem like this).

Thanks in advance for any help, 
R.

---

### Post by rocheteau on 2008-10-23
Sorry for the placement of the sticky in the above post - apparently a colon followed by a D is being seen as the sticky. The correct text should read "DBD" not "smileyBD".
Thanks, 
R.

---

### Post by OldGaf on 2011-04-18
> **rocheteau said:**
> Sorry for the placement of the sticky in the above post - apparently a colon followed by a D is being seen as the sticky. The correct text should read "DBD" not "smileyBD".
Thanks, 
R.

Ever solve this.....?

---

### Post by keezebub on 2012-02-09
> **OldGaf said:**
> Ever solve this.....?


I know it's been a while, but I had this same error, and I figured I would help whoever needed it.

Try 'sudo apt-get install libmysqlclient15-dev' to install the mysql_config executable, then using cpan to install the perl module.

---

### Post by Linux Dutchman on 2012-02-09
This is an very old thread. Probably the topic starter already updated his system to 10.04.3 Server edition. And maybe thinking of updating to 12.04. If so, his issue should be solved by updating to a much newer version.

---

