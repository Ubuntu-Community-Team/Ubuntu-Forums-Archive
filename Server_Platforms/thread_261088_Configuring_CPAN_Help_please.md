---
title: "Configuring CPAN? Help please"
date: 2006-09-19
forum: Server Platforms
---

### Post by JD_2020 on 2006-09-19
Hi -

I have a problem when trying to install DBD::mysql perl module through CPAN. Here is the error:

> 
Can't exec "mysql_config": No such file or directory at Makefile.PL line 451.
Can't exec "mysql_config": No such file or directory at Makefile.PL line 451.
Can't exec "mysql_config": No such file or directory at Makefile.PL line 451.
Can't exec "mysql_config": No such file or directory at Makefile.PL line 451.
Can't exec "mysql_config": No such file or directory at Makefile.PL line 451.
Can't exec "mysql_config": No such file or directory at Makefile.PL line 451.


I opened up the makefile and read some of the code, and it more or less looks in a few places for the mysql_config, and if you don't specify the path it makes its best guess. I know the path to my mysql_config, but have no way of entering it in via a flag since CPAN is doing this all for me.

So my question:

How do I configure CPAN so I can specify where my mysql_config file is?

Thanks!
-JD

---

### Post by bluefrog on 2006-09-20
not a direct answer to your question but well...

have a look in synaptic. dbd-mysql should be in there (universe repo most likely)

James

---

### Post by jhquentin on 2008-01-21
apt-get install libmysqlclient15-dev

---

