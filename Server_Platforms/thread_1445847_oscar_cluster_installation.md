---
title: "oscar cluster installation"
date: 2010-04-03
forum: Server Platforms
---

### Post by koorosh01 on 2010-04-03
hi friends ...
i want to install oscar cluster on my ubuntu 8.04 , so i added its repository from [http://svn.oscar.openclustergroup.org/trac/oscar/wiki/repoTesting]("http://svn.oscar.openclustergroup.org/trac/oscar/wiki/repoTesting") 
i added  repo from **Testing the development version** section .
and i followd each step . but the problem is this ..
when i use oscar-config --bootstrap i receive this error :

Initializing ODA: mysql
ERROR: Unknown ODA type ()
 at /usr/bin/oda line 886
koorosh01@koorosh01-desktop:~$ ERROR: Impossible to bootstrap the database at /usr/bin/oda line 887.
ERROR: Impossible to execute /usr/bin/oda --init mysql at /usr/bin/oscar-config line 99
ERROR: Impossible to install the server side of OSCAR
 at /usr/bin/oscar-config line 99
ERROR: Impossible to complete stage 2 of the bootstrap.
 at /usr/bin/oscar-config line 99
ERROR: Impossible to bootstrap OSCAR at /usr/bin/oscar-config line 100
	main::bootstrap() called at /usr/bin/oscar-config line 331
ERROR: Impossible to bootstrap OSCAR at /usr/bin/oscar-config line 332.

i must mention that i have mysql database . so if you have eny experience in installing oscar please help me.

thanx alot

---

### Post by KB1JWQ on 2010-04-03
You might have better luck pursuing an Oscar support vector; many folks here have never heard of it before.  I know I haven't. :-)

Good luck.

---

